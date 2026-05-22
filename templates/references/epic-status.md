# Epic status and lean jira board

## `docs/pm/jira/OVERVIEW.md` — Epics table

| ID | Epic | Status | Jira |
|----|------|--------|------|

**Status** (exact values): `TODO` | `IN_PROGRESS` | `DONE`

- **TODO** — queued; no story rows yet
- **IN_PROGRESS** — active; **stories** and **task files** only for this epic (default: one epic; multiple only if user says so — set `active_epics` in frontmatter)
- **DONE** — shipped or abandoned; remove story rows; keep epic row; task files stay in `tasks/done/`

## Stories table (same file)

Only rows for epics with `IN_PROGRESS` (or all listed in `active_epics`).

| ID | Epic | Story | Priority | Jira |
|----|------|-------|----------|------|

## Task files (not a table)

One markdown file per task under `docs/pm/jira/tasks/{todo|inprogress|done}/`. See `references/jira-task-file.md`.

## Rules

1. **Always** list all epics in `jira/OVERVIEW.md`.
2. **Only** add story rows + create task files for `IN_PROGRESS` epic(s).
3. When switching epic: old epic → `DONE`, remove its story rows from OVERVIEW, new epic → `IN_PROGRESS`, add new stories + task files in `tasks/todo/`.
4. Append planning events to `docs/pm/plan/CHANGELOG.md` — not inside `jira/`.
5. Jira holds full history; `tasks/done/` is the local archive of shipped work.
