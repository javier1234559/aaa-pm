# AAA PM — Agent Skills pack

[![skills.sh](https://skills.sh/b/javier1234559/aaa-pm)](https://skills.sh/javier1234559/aaa-pm)

Reusable **Agent Skills** for solo PO + Dev: **`docs/pm/`** + **Jira**. Ticket shapes in pack **`PROPOSAL.md`** (local markdown = Jira description).

| Folder | Contents |
| --- | --- |
| `skills/` | One skill per folder + `SKILL.md` |
| `templates/` | Scaffold + epic / story / task templates |
| `templates/examples/` | Filled examples (pack-only) |
| `SKILL.md` | Umbrella `aaa-pm` → `/aaa-pm-about` |
| `PROPOSAL.md` | Ticket templates, QA flow, PO skill bonus |

**Product repo after setup:**

- `docs/pm/` — brief, intake, plan, `jira/OVERVIEW.md`, **`jira/epics/{todo,inprogress,done}/`**, **`jira/stories/{todo,inprogress,done}/`**, `jira/tasks/`
- `docs/qa/ACCESS.md` — test access (staging, login)

## Skills (`/…`)

| Skill | Purpose |
| --- | --- |
| `aaa-pm-about` | Pack overview |
| `aaa-pm-setup` | Scaffold `docs/pm/` + `docs/qa/ACCESS.md` |
| `aaa-pm-plan` | Epic + story files (tasks when Dev asks or work starts) |
| `aaa-pm-push` | Jira create (full file body = description) |
| `aaa-pm-intake` | Feedback → raw-intake + updates |
| `aaa-pm-sync` | Pull new Jira tasks + todo-only status reconcile |
| `aaa-pm-task-start` | Pick task → inprogress → implementation plan |
| `aaa-pm-task-done` | Mark task done after review |
| `aaa-pm-task-add` | Add emergent tasks to a story |

Typical flow: **setup → plan → push** · **task-start → task-done** · **sync** (when dev 2 adds Jira tickets) · PO QA per **PROPOSAL.md**

## Install

```bash
npx skills add javier1234559/aaa-pm --skill '*' -y
```

**Local path:**

```bash
npx skills add ./.claude/skills/aaa-pm --skill '*' -y
```

## Update

```bash
npx skills update aaa-pm-about aaa-pm-setup aaa-pm-plan aaa-pm-push \
  aaa-pm-intake aaa-pm-sync aaa-pm-task-start aaa-pm-task-done aaa-pm-task-add \
  aaa-pm -y
```

`npx skills update` refreshes agent skills only — not `docs/pm/` in product repos.

## Relation to `aaa-qa`

| Pack | Scope |
| --- | --- |
| **`aaa-pm`** | `docs/pm/` + `docs/qa/ACCESS.md` |
| **`aaa-qa`** | Extended `docs/qa/` (test cases, etc.) — optional |

## Links

- [skills.sh — Docs](https://www.skills.sh/docs) · [Agent Skills spec](https://agentskills.io/specification)
