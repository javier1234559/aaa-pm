---
name: aaa-pm-about
description: >-
  Help for the aaa-pm skill pack — docs/pm layout, workflow, templates, and examples.
  Use when user asks aaa-pm help, how to use, what skill next, or about project brief / jira pm.
metadata:
  pack: aaa-pm
disable-model-invocation: true
---

# AAA PM — about

Solo PM workflow for one developer: **`docs/pm/`** + **Jira**. Works in **any** product repo.

## Pack root

Folder containing `templates/` and `skills/`:

- Published: `aaa-pm/`
- Installed: e.g. `.agents/skills/aaa-pm/`

Read `{pack-root}/templates/…` and `templates/references/paths.md` — never assume root `PROJECT_BRIEF.md` on new projects.

## Source of truth

| Artifact | Role |
|----------|------|
| `docs/pm/project-brief/OVERVIEW.md` | Product — goal, features, scope |
| `docs/pm/jira/OVERVIEW.md` | Epics + active stories |
| `docs/pm/jira/tasks/{todo,inprogress,done}/` | One file per task (push → Jira) |
| `docs/pm/intake/raw-intake/` | Verbatim pasted feedback |
| `docs/pm/plan/CHANGELOG.md` | Plan version / push events |
| **Jira** | Execution status — sync moves task files |

Gate: `brief_status: complete` on project brief (`/aaa-pm-setup`).

## Skills

| Skill | When |
| --- | --- |
| `/aaa-pm-about` | This help |
| `/aaa-pm-setup` | Scaffold `docs/pm/` or migrate legacy brief |
| `/aaa-pm-plan` | Epics, stories, task files in `tasks/todo/` |
| `/aaa-pm-push` | Create Jira from task files |
| `/aaa-pm-intake` | Paste stakeholder feedback |
| `/aaa-pm-sync` | Jira → move task files + OVERVIEW |
| `/aaa-pm-task-doing` | Issue URL/key → dev context file |

## Flows

**New project:** `setup` → fill brief → `plan` → `push`

**Daily:** `task-doing` + implementation skill in new chat

**Feedback:** `intake` → small: task file + `push` delta · large: `plan`

**Board changed in Jira:** `sync`

## Plan shape

| Level | Where |
|-------|--------|
| **Epic** | `jira/OVERVIEW.md` — all statuses |
| **Story** | `jira/OVERVIEW.md` — active epic(s) only |
| **Task** | `jira/tasks/todo/` (etc.) — one markdown file each |

Rules: `templates/references/epic-status.md`, `templates/references/jira-task-file.md`

Examples (pack-only): `templates/examples/example-jira-overview.md`, `example-task-file.md`, `templates/examples/aaa-portfolio/`

## Pick one

- **A** — `/aaa-pm-setup`
- **B** — `/aaa-pm-plan`
- **C** — `/aaa-pm-push`
- **D** — `/aaa-pm-intake`
- **E** — `/aaa-pm-sync`
- **F** — `/aaa-pm-task-doing`
- **G** — Read `templates/examples/` for samples
