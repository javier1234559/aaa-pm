# Epic status and lean jira board

## `docs/pm/jira/OVERVIEW.md` — index only

Epic and story **detail** live in separate files. OVERVIEW holds tables + task counts + sync note.

### Epics table

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|

**Status** (exact values): `TODO` | `IN_PROGRESS` | `DONE`

- **TODO** — queued; no story files for this epic
- **IN_PROGRESS** — active; **story files** in `jira/stories/` (default: one epic in `active_epics`). Task files optional — added when Dev starts work, not at plan time.
- **DONE** — shipped; remove active story rows; keep epic row + `jira/epics/E-NN-*.md`; tasks stay in `tasks/done/`

### Active stories table

Only rows for epics with `IN_PROGRESS` (or all in `active_epics`).

| ID | Epic | Story | Priority | File | Jira |
|----|------|-------|----------|------|------|

Detail: `docs/pm/jira/stories/S-NN-*.md` — acceptance criteria, Handoff QA, Definition of Done.

**Sizing:** one story per user benefit — see `plan-story-first.md`. Do not use one mega-story with many sub-tasks as a substitute for proper story split.

### Epic files

`docs/pm/jira/epics/E-NN-kebab-title.md` — body = Jira Epic description.

### Task files

`docs/pm/jira/tasks/{todo|inprogress|done}/` — see `references/jira-task-file.md`. Created by Dev/PO or `/aaa-pm-intake`, not by default `/aaa-pm-plan`.

## Rules

1. **Always** list all epics on OVERVIEW + one file per epic in `jira/epics/`.
2. **Only** add **story files** for `IN_PROGRESS` epic(s) during plan.
3. **Do not** auto-create task files during plan — see `plan-story-first.md`.
4. When switching epic: old → `DONE`, remove its story rows; new → `IN_PROGRESS`, new story files (tasks only if user asks).
5. Planning events → `docs/pm/plan/CHANGELOG.md` only.
6. `docs/qa/ACCESS.md` — shared test access; stories link Handoff QA here.
