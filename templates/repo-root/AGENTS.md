# AGENTS.md — AAA PM (`docs/pm/`)

**On open:** Ask what the user needs — **setup**, **brief**, **plan**, **push**, **intake**, **sync**, or **task-doing**. Run **only** the matching `/aaa-pm-*` skill.

**Skills:** `/aaa-pm-about` · `/aaa-pm-setup` · `/aaa-pm-plan` · `/aaa-pm-push` · `/aaa-pm-intake` · `/aaa-pm-sync` · `/aaa-pm-task-doing`

**Paths:** All PM artifacts live under `docs/pm/` — see `README.md`.

| Folder | Role |
|--------|------|
| `project-brief/` | Product — goal, features, scope (`OVERVIEW.md` + `CHANGELOG.md`) |
| `intake/` | Pasted feedback index + `raw-intake/` verbatim files |
| `plan/` | Planning history (`CHANGELOG.md` only) |
| `jira/` | Board — `OVERVIEW.md` (epics + active stories) + `tasks/{todo,inprogress,done}/` |

**Gate:** `docs/pm/project-brief/OVERVIEW.md` frontmatter `brief_status: complete` (set by `/aaa-pm-setup`).

**Git push:** After work, ask: *"Update the repo so the team can use these docs?"* Only if **yes**: `git pull` then `git push`.

**Relation to `aaa-qa`:** QA test docs live in `docs/qa/` — separate pack; link from brief §Assets if needed.
