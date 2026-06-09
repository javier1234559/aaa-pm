---
name: aaa-pm-sync
description: >-
  Sync Jira into docs/pm/jira — move task files between todo/inprogress/done, update OVERVIEW
  keys and sync note. Use when user says sync jira or refresh from jira.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — sync

## Gate

Read `templates/references/gate.md`.

## Goal

Reconcile **`docs/pm/jira/`** with live Jira. Jira is truth for **status**; brief is truth for **product**; task files + OVERVIEW are **working plan**.

## Atlassian MCP

1. Read MCP schemas before calling.
2. Fetch issues for `jira_project_key` (JQL e.g. `project = KEY ORDER BY updated DESC`).
3. Match issues to local artifacts:
   - Task files: frontmatter `jira:` key, else `Local ID: T-XX` in body
   - Epic files: `docs/pm/jira/epics/` — frontmatter `jira:` or `Local ID: E-XX`
   - Story files: `docs/pm/jira/stories/` — frontmatter `jira:` or `Local ID: S-XX`
   - OVERVIEW epic/story rows: `Jira` column (sync with file frontmatter)

## Updates

### Task files

| Jira status (typical) | Move file to |
|----------------------|--------------|
| To Do / Backlog | `tasks/todo/` |
| In Progress | `tasks/inprogress/` |
| Done | `tasks/done/` |

Use **move** (same filename), do not duplicate files.

### `docs/pm/jira/OVERVIEW.md`

1. Fill empty `Jira` cells when match is confident.
2. Replace **## Sync note** with:

```markdown
## Sync note (YYYY-MM-DD)
- Matched: N | Orphan in Jira: N | Local without Jira: N
- Moves: T-01 todo→inprogress, …
```

3. Refresh **Task board** counts.
4. Set `last_synced_at` in frontmatter.

### Do not

- Auto-edit `docs/pm/project-brief/OVERVIEW.md` §Goal / §Features.
- Auto-delete task files or epic rows.

## Report in chat

- Orphans (in Jira, no local file/row)
- Local without Jira (unpushed or deleted in Jira)
- Status changes

If >30% mismatch → suggest **`/aaa-pm-plan`** or manual cleanup.

## After

> **`/aaa-pm-task-doing`** to implement. Missing tickets → **`/aaa-pm-push`** (delta).
