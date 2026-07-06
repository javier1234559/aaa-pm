# Epic status and lean jira board

## `docs/pm/jira/OVERVIEW.md` — index only

Epic, story, and task **detail** live in separate files under status folders. OVERVIEW holds tables + board counts + sync note.

### Epics table

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|

**Status** (must match folder): `TODO` | `IN_PROGRESS` | `DONE`

| Folder | Status |
|--------|--------|
| `epics/todo/` | `TODO` — queued; no story files yet |
| `epics/inprogress/` | `IN_PROGRESS` — active; story files in `jira/stories/` (default: one epic in `active_epics`) |
| `epics/done/` | `DONE` — shipped; stories in `stories/done/`; tasks in `tasks/done/` |

### Epic board (counts)

| Todo | In progress | Done |
|------|-------------|------|
| N | N | N |

Counts: `.md` files in `epics/todo`, `inprogress`, `done` (exclude README, `_template.md`).

### Stories table

All stories for active and shipped epics — not only in-flight.

| ID | Epic | Story | Priority | File | Jira |
|----|------|-------|----------|------|------|

Detail: `docs/pm/jira/stories/{todo,inprogress,done}/S-NN-*.md`

### Story board (counts)

| Todo | In progress | Done |
|------|-------------|------|
| N | N | N |

Counts: `.md` files in `stories/todo`, `inprogress`, `done` (exclude README, `_template.md`).

### Task board (counts)

| Todo | In progress | Done |
|------|-------------|------|
| N | N | N |

Counts: `.md` files in `tasks/todo`, `inprogress`, `done` (exclude README).

**Sizing:** one story per user benefit — see `plan-story-first.md`. Do not use one mega-story with many sub-tasks as a substitute for proper story split.

## Rules

1. **Always** list all epics on OVERVIEW + one file per epic in `jira/epics/{folder}/`.
2. **Only** add **story files** for `inprogress/` epic(s) during plan (into `stories/todo/`).
3. **Do not** auto-create task files during plan — see `plan-story-first.md`.
4. When switching epic: old file → `epics/done/`, its stories → `stories/done/`; new file → `epics/inprogress/`, new story files in `stories/todo/`.
5. Planning events → `docs/pm/plan/CHANGELOG.md` only.
6. `docs/qa/ACCESS.md` — shared test access; stories link Handoff QA here.
7. Emergent tasks during implementation → **`/aaa-pm-task-add`** (no full re-plan).
