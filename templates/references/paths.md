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
| `docs/pm/jira/OVERVIEW.md` | Board index — epic/story/task tables + counts, sync note |
| `docs/pm/jira/epics/{todo,inprogress,done}/` | One file per epic — body = Jira Epic description |
| `docs/pm/jira/stories/{todo,inprogress,done}/` | One file per story — AC, Handoff QA, DoD |
| `docs/pm/jira/tasks/{todo,inprogress,done}/` | Task files — Dev/PO when work starts (not auto at plan) |
| `docs/qa/ACCESS.md` | Staging URL, login, seed data — once per project |

**Ticket rule:** local markdown body = Jira description (see pack `PROPOSAL.md`).

**Folder = status** for epics, stories, and tasks. OVERVIEW tables mirror folder counts.

**Legacy:** flat `jira/epics/E-*.md` or `jira/stories/S-*.md` — see `migrate-epic-story-folders.md`.

**Legacy:** `PROJECT_BRIEF.md` at repo root — run **`/aaa-pm-setup`** migrate option.

**Pack-only:** `{pack-root}/templates/examples/`

**Sync:** `templates/references/sync-matching.md` — ID rules, incremental JQL, todo-only default.
