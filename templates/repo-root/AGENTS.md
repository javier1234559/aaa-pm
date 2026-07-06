# AGENTS.md — AAA PM (`docs/pm/`)

**On open:** Ask what the user needs — **setup**, **brief**, **plan**, **push**, **intake**, **sync**, **task-start**, **task-done**, or **task-add**. Run **only** the matching `/aaa-pm-*` skill.

**Skills:** `/aaa-pm-about` · `/aaa-pm-setup` · `/aaa-pm-plan` · `/aaa-pm-push` · `/aaa-pm-intake` · `/aaa-pm-sync` · `/aaa-pm-task-start` · `/aaa-pm-task-done` · `/aaa-pm-task-add`

**Paths:** All PM artifacts under `docs/pm/` — see `README.md`. Ticket templates: aaa-pm pack **`PROPOSAL.md`**.

| Folder | Role |
|--------|------|
| `project-brief/` | Product — goal, features, scope |
| `intake/` | Pasted feedback + `raw-intake/` |
| `plan/` | Planning history (`CHANGELOG.md`) |
| `jira/OVERVIEW.md` | Board index — tables + board counts + sync note |
| `jira/epics/{todo,inprogress,done}/` | One file per epic — folder = status |
| `jira/stories/{todo,inprogress,done}/` | One file per story — folder = status |
| `jira/tasks/{todo,inprogress,done}/` | One file per task |

**`docs/qa/ACCESS.md`** — staging, login, seed (once per project).

**Gate:** `brief_status: complete` on project brief (`/aaa-pm-setup`).

**Rule:** local markdown = Jira description. **Folder = status** for epics, stories, tasks.

**Dev loop:** `/aaa-pm-task-start` → approve plan → implement → `/aaa-pm-task-done`

**Git push:** After work, ask: *"Update the repo so the team can use these docs?"* Only if **yes**: `git pull` then `git push`.
