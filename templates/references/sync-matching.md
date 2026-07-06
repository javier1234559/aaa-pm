# Sync matching rules (Jira ↔ local)

Read before **`/aaa-pm-sync`**. Local-first workflow: **`/aaa-pm-push`** creates Jira; **`/aaa-pm-sync`** pulls **new** tickets and reconciles **todo** items.

## Local ID format

| Type | Pattern | Filename | Frontmatter |
|------|---------|----------|-------------|
| Epic | `E-01` … `E-99` | `E-01-kebab-title.md` | `id: E-01` |
| Story | `S-01` … `S-99` | `S-01-kebab-title.md` | `id: S-01` |
| Task | `T-01` … `T-99` | `T-01-kebab-title.md` | `id: T-01` |

**Push rule:** every pushed file must include in the Jira description body:

```text
**Local ID:** T-01
```

(or `Local ID: T-01` — sync accepts both)

## Jira key format

`{PROJECT_KEY}-{number}` e.g. `AAAP-43` — stored in frontmatter `jira:` and OVERVIEW table **Jira** column.

## Match priority (highest wins)

When linking a Jira issue to a local file:

1. **Exact `jira:` key** — frontmatter on any epic/story/task file
2. **OVERVIEW Jira column** — row for same Local ID
3. **`Local ID:` in Jira description** — regex `(?i)local\s+id:\s*(E|S|T)-\d+`
4. **Filename stem** — `T-15-foo.md` → Local ID `T-15` (only if single match)

## Known set (build at start of every sync)

Scan **all** folders (not only todo) to build:

- `known_jira_keys` — every non-empty `jira:` + OVERVIEW Jira cells
- `known_local_ids` — every `id:` frontmatter + filename `E|S|T-NN` stems

A Jira issue is **new (unlinked)** when its key ∉ `known_jira_keys` AND no `Local ID:` in its description matches a file that already has a different `jira:`.

## Default sync scope — **todo only**

| Action | Scope |
|--------|--------|
| Pull new Jira tasks → local file | Yes — always land in `tasks/todo/` |
| Backfill `jira:` on local file | Only files in `*/todo/` missing `jira:` |
| Move folder by Jira status | Only files currently in `*/todo/` |
| Touch `inprogress/` or `done/` | **No** (unless user says **sync full**) |

**Why:** `task-start` / `task-done` own inprogress and done locally. Full board reconcile is opt-in.

## JQL (incremental)

Read `last_synced_at` from `docs/pm/jira/OVERVIEW.md` frontmatter.

**Default (inbound new tasks):**

```text
project = {KEY} AND issuetype in (Task, "Sub-task") AND updated >= "{last_synced_at}"
ORDER BY updated DESC
```

If `last_synced_at` is null → last 14 days:

```text
project = {KEY} AND issuetype in (Task, "Sub-task") AND created >= -14d
ORDER BY created DESC
```

**Status check (todo items with `jira:` filled):**

Fetch by key list only — do not scan whole project:

```text
key in (AAAP-1, AAAP-2, …)
```

Cap batch at 50 keys; split if more todo items.

## Inbound new task (created on Jira by another dev)

When Jira issue is unlinked:

1. Allocate next `T-NN` (max existing + 1).
2. Create `docs/pm/jira/tasks/todo/T-NN-kebab-from-summary.md`.
3. Set frontmatter `jira: {KEY}` immediately.
4. Resolve parent Story from Jira `parent` → match local `S-XX` via parent's `jira:` or `Local ID:`.
5. Set `epic:` from story frontmatter.
6. Body: Jira summary + description + `**Local ID:** T-NN`.
7. Append OVERVIEW § Stories link if needed; refresh task board count.
8. Set `jira_pushed: true` is already true for inbound (key exists on Jira).

**Confirm with user** if more than 3 new inbound files in one run.

## Status mapping (todo items only)

| Jira status (typical) | Move local file to |
|----------------------|-------------------|
| To Do / Backlog | stay in `todo/` |
| In Progress | `inprogress/` |
| Done | `done/` |

Same mapping for epics/stories/tasks when in default todo-only mode.

## Needs push (not sync)

Local file in `todo/` with **empty `jira:`** and no matching Jira issue by Local ID → report:

```text
Needs push: T-03, S-07 — run /aaa-pm-push
```

Do not create duplicate Jira issues during sync.

## Full sync

User says **`/aaa-pm-sync full`** → reconcile **all** folders (inprogress, done included). Use after long absence or board drift.
