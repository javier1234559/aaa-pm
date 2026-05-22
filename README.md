# AAA PM — Agent Skills pack

[![skills.sh](https://skills.sh/b/javier1234559/aaa-pm)](https://skills.sh/javier1234559/aaa-pm)

Reusable **Agent Skills** for solo PM: **`docs/pm/`** in the product repo + **Jira** execution. Install with the [skills CLI](https://github.com/vercel-labs/skills), then invoke with `/skill-name`. GitHub: **`javier1234559/aaa-pm`** (or `Automation-Architecture/aaa-portfolio` monorepo path `aaa-pm/`).

All skills use the **`aaa-pm-`** prefix to avoid clashing with other packs (e.g. `aaa-qa-`).

| Folder | Contents |
| --- | --- |
| `skills/` | One skill per folder + `SKILL.md` |
| `templates/` | Scaffold copied to product repos (`docs/pm/`) + epic / story / task templates |
| `templates/examples/` | Filled examples (pack-only; agents read for context) |
| `SKILL.md` | Umbrella `aaa-pm` → start with `/aaa-pm-about` |

Full conventions: [`templates/repo-root/AGENTS.md`](templates/repo-root/AGENTS.md).

**Product repo after setup:** `docs/pm/` — `project-brief/`, `intake/raw-intake/`, `plan/CHANGELOG.md`, `jira/OVERVIEW.md` + `jira/tasks/{todo,inprogress,done}/`.

## Skills (`/…`)

| Skill | Purpose |
| --- | --- |
| `aaa-pm-about` | Pack overview and which skill to run |
| `aaa-pm-setup` | Create empty `docs/pm/` scaffold (any project) |
| `aaa-pm-plan` | Epics + stories on `jira/OVERVIEW` + task files in `tasks/todo/` |
| `aaa-pm-push` | Create Jira from plan (Atlassian MCP) |
| `aaa-pm-intake` | Paste feedback → `raw-intake/` + brief / jira updates |
| `aaa-pm-sync` | Jira status → move task files + refresh `OVERVIEW` |
| `aaa-pm-task-doing` | One ticket → `.cursor/context/<KEY>.md` |

Typical flow: **setup → plan → push** · daily: **task-doing** · feedback: **intake** · board drift: **sync**

## Install

```bash
npx skills add javier1234559/aaa-pm --skill '*' -y
```

**Local path (before publish):**

```bash
npx skills add ./aaa-pm --skill '*' -y
```

In the product repo: **`/aaa-pm-setup`**, then the skills above.

Legacy root **`PROJECT_BRIEF.md`**: setup can migrate → `docs/pm/` — see [`templates/references/migrate-legacy-brief.md`](templates/references/migrate-legacy-brief.md).

## Update

```bash
npx skills update aaa-pm-about aaa-pm-setup aaa-pm-plan aaa-pm-push \
  aaa-pm-intake aaa-pm-sync aaa-pm-task-doing aaa-pm -y
```

`npx skills update` refreshes agent skills only — not `docs/pm/` in product repos.

## Relation to `aaa-qa`

| Pack | Scope |
| --- | --- |
| **`aaa-pm`** | `docs/pm/` — brief, intake, plan log, Jira task files |
| **`aaa-qa`** | `docs/qa/` — charter, requirements, dev workflows, test cases |

Independent installs; link from brief §Assets if both packs are used.

## Links

- [skills.sh — Docs](https://www.skills.sh/docs) · [skills CLI](https://github.com/vercel-labs/skills) · [Agent Skills spec](https://agentskills.io/specification)
