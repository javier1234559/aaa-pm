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
| `docs/pm/jira/OVERVIEW.md` | Board index — epic/story tables, task counts, sync note |
| `docs/pm/jira/epics/E-NN-*.md` | One file per epic — body = Jira Epic description |
| `docs/pm/jira/stories/S-NN-*.md` | One file per story — AC, Handoff QA, DoD |
| `docs/pm/jira/tasks/todo/` | Task files not started / Jira To Do |
| `docs/pm/jira/tasks/inprogress/` | Task files in flight / Jira In Progress |
| `docs/pm/jira/tasks/done/` | Task files completed / Jira Done |
| `docs/qa/ACCESS.md` | Staging URL, login, seed data — once per project |

**Ticket rule:** local markdown body = Jira description (see pack `PROPOSAL.md`).

**Legacy:** `PROJECT_BRIEF.md` at repo root — run **`/aaa-pm-setup`** migrate option.

**Pack-only:** `{pack-root}/templates/examples/`
