# Canonical paths (product repo)

All `aaa-pm-*` skills read and write under **`docs/pm/`** unless migrating legacy `PROJECT_BRIEF.md`.

| Path | Purpose |
|------|---------|
| `docs/pm/AGENTS.md` | Mode rules for agents (copied on setup) |
| `docs/pm/README.md` | Human index |
| `docs/pm/project-brief/OVERVIEW.md` | Product truth — goal, features, scope |
| `docs/pm/project-brief/CHANGELOG.md` | Brief change history |
| `docs/pm/intake/OVERVIEW.md` | Index of pasted feedback |
| `docs/pm/intake/raw-intake/<file>.md` | Verbatim intake (one paste per file) |
| `docs/pm/plan/CHANGELOG.md` | Plan / push / re-slice events only |
| `docs/pm/jira/OVERVIEW.md` | Epics (full) + active stories + board summary |
| `docs/pm/jira/tasks/todo/` | Task files not started / Jira To Do |
| `docs/pm/jira/tasks/inprogress/` | Task files in flight / Jira In Progress |
| `docs/pm/jira/tasks/done/` | Task files completed / Jira Done |

**Legacy:** `PROJECT_BRIEF.md` at repo root — run **`/aaa-pm-setup`** migrate option; do not use for new projects.

**Pack-only (never copied to product repos):** `{pack-root}/templates/examples/`
