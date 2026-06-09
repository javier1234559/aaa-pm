# Epic status and lean jira board

## `docs/pm/jira/OVERVIEW.md` — index only

Epic and story **detail** live in separate files. OVERVIEW holds tables + task counts + sync note.

### Epics table

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|

**Status** (exact values): `TODO` | `IN_PROGRESS` | `DONE`

- **TODO** — queued; no story files for this epic
- **IN_PROGRESS** — active; **story files** in `jira/stories/` + **task files** (default: one epic in `active_epics`)
- **DONE** — shipped; remove active story rows; keep epic row + `jira/epics/E-NN-*.md`; tasks stay in `tasks/done/`

### Active stories table

Only rows for epics with `IN_PROGRESS` (or all in `active_epics`).

| ID | Epic | Story | Priority | File | Jira |
|----|------|-------|----------|------|------|

Detail: `docs/pm/jira/stories/S-NN-*.md` — acceptance criteria, Handoff QA, Definition of Done.

### Epic files

`docs/pm/jira/epics/E-NN-kebab-title.md` — body = Jira Epic description.

### Task files

`docs/pm/jira/tasks/{todo|inprogress|done}/` — see `references/jira-task-file.md`.

## Rules

1. **Always** list all epics on OVERVIEW + one file per epic in `jira/epics/`.
2. **Only** add story files + tasks for `IN_PROGRESS` epic(s).
3. When switching epic: old → `DONE`, remove its story rows; new → `IN_PROGRESS`, new story + task files.
4. Planning events → `docs/pm/plan/CHANGELOG.md` only.
5. `docs/qa/ACCESS.md` — shared test access; stories link Handoff QA here.
