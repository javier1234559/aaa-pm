---
name: aaa-pm-sync
description: >-
  Incremental Jira sync — pull new tasks from Jira into tasks/todo, backfill jira keys, reconcile
  todo folder status. Default is todo-only; use "sync full" for all folders. Use when dev 2 adds
  Jira tickets or user says sync jira.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — sync

Incremental reconcile: **Jira → local** for new tickets; **todo-only** status moves by default.

## Gate

Read `templates/references/gate.md`.

Read **`templates/references/sync-matching.md`** (mandatory — ID rules, JQL, scope).

Also: `jira-epic-file.md`, `jira-story-file.md`, `jira-task-file.md`.

If flat epic/story layout → `migrate-epic-story-folders.md` first.

## Modes

| Mode | Trigger | Scope |
|------|---------|--------|
| **Default** | `/aaa-pm-sync` | **Todo folders only** + inbound new Jira tasks |
| **Full** | `/aaa-pm-sync full` | All `todo/inprogress/done` folders |

Tell user which mode ran in the report.

---

## Step 0 — Build known set

Scan **all** `docs/pm/jira/` files (every folder) plus `OVERVIEW.md` tables:

- `known_jira_keys` — non-empty `jira:` + Jira column cells
- `known_local_ids` — `id:` frontmatter + `E|S|T-NN` filename stems
- `todo_with_jira` — files in `*/todo/` where `jira:` is set → queue for status fetch
- `todo_without_jira` — files in `*/todo/` where `jira:` empty → queue for push report

---

## Step 1 — Needs push (local → Jira, not sync)

For each file in `todo_without_jira`:

- Search Jira (by Local ID in description) for existing issue with same `Local ID: T-XX` / `S-XX` / `E-XX`
- **Found** → **backfill** `jira:` on local file + OVERVIEW row (link only, do not create)
- **Not found** → add to **Needs push** list → user runs **`/aaa-pm-push`**

Never create Jira issues in sync.

---

## Step 2 — Inbound new tasks (Jira → local)

**Default mode only pulls Task / Sub-task** (dev 2 adding work on Jira).

### JQL

Read `last_synced_at` from OVERVIEW frontmatter.

```text
project = {KEY} AND issuetype in (Task, "Sub-task") AND updated >= "{last_synced_at}"
ORDER BY updated DESC
```

If `last_synced_at` null:

```text
project = {KEY} AND issuetype in (Task, "Sub-task") AND created >= -14d
ORDER BY created DESC
```

### Per Jira issue

Skip if key ∈ `known_jira_keys`.

Else try match (see `sync-matching.md`):

1. `Local ID:` in description → link/backfill existing local file
2. No local file → **new inbound**

### New inbound file

Create `docs/pm/jira/tasks/todo/T-NN-kebab-from-summary.md`:

```markdown
---
id: T-NN
story: S-XX
epic: E-XX
type: FEAT
jira: AAAP-99
priority: Should
estimate:
---

# {Jira summary}

**Story:** S-XX — …
**Epic:** E-XX — …
**Jira:** AAAP-99
**Local ID:** T-NN
**Source:** inbound sync {date}

## Context
Created on Jira — pulled by /aaa-pm-sync. Review and fill Dev sections.

## What to build
(from Jira description)

## Done when
-

## Out of scope
-
```

- Parent story: resolve from Jira `parent` field → local `S-XX` via parent's `jira:` or `Local ID:`
- If parent story unknown → leave `story:` blank; report for manual link
- Allocate `T-NN` = max existing + 1

**If >3 new inbound files** → show table and wait for user confirm before creating.

Epic/Story issues on Jira without local match → report as **orphan** (do not auto-create; suggest **`/aaa-pm-plan`** or manual).

---

## Step 3 — Status reconcile

### Default (todo only)

For each file in `epics/todo/`, `stories/todo/`, `tasks/todo/` with `jira:` set:

Fetch issue status (batch `key in (...)` — max 50 per query).

| Jira status | Action |
|-------------|--------|
| To Do / Backlog | no move |
| In Progress | move → `inprogress/` |
| Done | move → `done/` |

Update OVERVIEW status columns + board counts. Update `active_epics` if epic moved.

**Do not** move files in `inprogress/` or `done/` in default mode.

### Full mode

Same status mapping for **all** folders. Report all moves.

---

## Step 4 — Update OVERVIEW

1. Fill empty Jira cells when backfill/link is confident.
2. Replace **## Sync note**:

```markdown
## Sync note (YYYY-MM-DD) — todo-only | full
- Mode: todo-only
- Known keys: N | Inbound new: N | Backfilled jira: N | Todo status moves: N
- Needs push: T-03, … (or none)
- Orphans on Jira: AAAP-50 (Story, no local) — …
- Inbound: T-18 ← AAAP-99, …
```

3. Refresh Epic / Story / Task board counts.
4. Set `last_synced_at` to now (ISO 8601) in frontmatter.

Append one line to `docs/pm/plan/CHANGELOG.md` if inbound > 0 or backfill > 0.

---

## Atlassian MCP

1. Read MCP schemas before calling.
2. Prefer **targeted JQL** and **key-in batches** — avoid fetching entire project every run.
3. Do not edit `project-brief/OVERVIEW.md` §Goal / §Features.
4. Do not delete local files.

---

## Report in chat

Always show:

| Bucket | Items |
|--------|--------|
| **Inbound new** | T-18 ← AAAP-99 "…" |
| **Backfilled jira:** | T-03 ← AAAP-12 |
| **Todo → inprogress** | … |
| **Needs push** | … → `/aaa-pm-push` |
| **Orphans** | Jira keys with no local file |
| **Skipped** | inprogress/done (todo-only mode) |

If >30% of todo items mismatch → suggest **`/aaa-pm-sync full`** or cleanup.

---

## After

> New inbound tasks: review file, then **`/aaa-pm-task-start`**. Unpushed local: **`/aaa-pm-push`**.
