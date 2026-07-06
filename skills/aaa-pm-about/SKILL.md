---
name: aaa-pm-about
description: >-
  Help for the aaa-pm skill pack — docs/pm layout, epics/stories/tasks, workflow, PROPOSAL templates.
  Use when user asks aaa-pm help, PO workflow, or what skill next.
metadata:
  pack: aaa-pm
disable-model-invocation: true
---

# AAA PM — about

Solo PO + Dev workflow: **`docs/pm/`** + **Jira**. Ticket shapes: pack **`PROPOSAL.md`** (`{pack-root}/PROPOSAL.md`).

## Pack root

`{pack-root}/templates/` — see `templates/references/paths.md`.

## Source of truth

| Artifact | Role |
|----------|------|
| `docs/pm/project-brief/OVERVIEW.md` | Product — goal, features, scope |
| `docs/pm/jira/OVERVIEW.md` | Board index — tables + board counts + sync note |
| `docs/pm/jira/epics/{todo,inprogress,done}/` | One epic per file — folder = status |
| `docs/pm/jira/stories/{todo,inprogress,done}/` | One story per file — folder = status |
| `docs/pm/jira/tasks/{todo,inprogress,done}/` | One task per file |
| `docs/qa/ACCESS.md` | Staging, login, seed (once per project) |
| `docs/pm/intake/raw-intake/` | Verbatim feedback |
| `docs/pm/plan/CHANGELOG.md` | Plan / push events |
| **Jira** | Execution status — `/aaa-pm-sync` moves files between folders |

Gate: `brief_status: complete` on project brief (`/aaa-pm-setup`).

**Rule:** local markdown = Jira description (no shortened paste block).

**Folder = status** for epics, stories, and tasks.

## Skills

| Skill | When |
| --- | --- |
| `/aaa-pm-about` | This help |
| `/aaa-pm-setup` | Scaffold `docs/pm/` + `docs/qa/ACCESS.md` |
| `/aaa-pm-plan` | Epic + story files (tasks deferred unless user asks) |
| `/aaa-pm-push` | Create Jira from files |
| `/aaa-pm-intake` | Stakeholder feedback |
| `/aaa-pm-sync` | Pull new Jira tasks + todo-only reconcile (`sync full` for all folders) |
| `/aaa-pm-task-start` | Pick task → inprogress → plan for approval |
| `/aaa-pm-task-done` | After review → move task to done |
| `/aaa-pm-task-add` | Add emergent tasks to a story |

## Flows

**New project:** `setup` → fill brief → `plan` → `push`

**Daily (Dev):** `task-start` → review plan → implement → `task-done`

**Mid-implementation:** `task-add` when more tasks emerge · `push` (delta) for new Jira keys

**PO:** `intake` · `plan` + `push` · `sync` on a schedule · QA per PROPOSAL (Handoff → AC → DoD)

**Board changed in Jira:** `sync` (default: todo-only) · `sync full` after long drift

## Plan shape

| Level | When created | Where |
|-------|----------------|--------|
| **Epic** | `/aaa-pm-plan` | `jira/epics/{todo,inprogress,done}/` + row on OVERVIEW |
| **Story** | `/aaa-pm-plan` (one per user benefit) | `jira/stories/todo/` (+ inprogress/done as work progresses) |
| **Task** | Dev starts work or `/aaa-pm-task-add` — **not** auto at plan | `jira/tasks/todo/` etc. |

**Stories first:** see `templates/references/plan-story-first.md`.

Rules: `templates/references/epic-status.md`, `templates/references/sync-matching.md`, `templates/references/jira-epic-file.md`, `templates/references/jira-story-file.md`, `templates/references/jira-task-file.md`

Examples (pack-only): `templates/examples/`

PO skill cheat sheet: **`PROPOSAL.md`** § Bonus — PO workflow using AI skills.

## Pick one

- **A** — `/aaa-pm-setup`
- **B** — `/aaa-pm-plan`
- **C** — `/aaa-pm-push`
- **D** — `/aaa-pm-intake`
- **E** — `/aaa-pm-sync`
- **F** — `/aaa-pm-task-start`
- **G** — `/aaa-pm-task-done`
- **H** — `/aaa-pm-task-add`
- **I** — Read `PROPOSAL.md` + `templates/examples/`
