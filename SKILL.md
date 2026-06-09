---
name: aaa-pm
description: >-
  AAA PM skill pack — docs/pm/ (brief, intake, plan, jira epics/stories/tasks) + Jira for solo PO/Dev.
  Ticket content matches PROPOSAL.md (local = Jira). Start /aaa-pm-about then /aaa-pm-setup.
---

# aaa-pm

Container skill for the **AAA PM** pack. All commands use the **`aaa-pm-`** prefix.

## Start here

1. **`/aaa-pm-about`** — layout, workflow, skill list.
2. **`/aaa-pm-setup`** — scaffold **`docs/pm/`** (+ **`docs/qa/ACCESS.md`**) in the product repo.
3. **`/aaa-pm-plan`** — epics, stories, tasks from the brief.
4. **`/aaa-pm-push`** — create Jira from local files (full markdown = Jira description).

Ticket templates and QA flow (Handoff QA, Definition of Done, ACCESS): **`{pack-root}/PROPOSAL.md`** and `templates/`.

## `docs/pm/` layout

| Path | Purpose |
|------|---------|
| `project-brief/OVERVIEW.md` | Product truth — goal, features, scope |
| `jira/OVERVIEW.md` | Board index — epic/story tables, task counts, sync note |
| `jira/epics/E-NN-*.md` | **One file per epic** — full epic body (push → Jira Epic) |
| `jira/stories/S-NN-*.md` | **One file per story** — AC, Handoff QA, DoD (push → Jira Story) |
| `jira/tasks/{todo,inprogress,done}/` | **One file per task** — Dev detail (push → Jira Task) |
| `intake/raw-intake/` | Verbatim stakeholder paste |
| `plan/CHANGELOG.md` | Plan / push events |

**`docs/qa/ACCESS.md`** — staging URL, login, seed data (once per project). Stories link here; do not repeat login on every story.

## Rules (PROPOSAL-aligned)

- **Local markdown = Jira description** — no separate “paste on push” block.
- **Epic** — outcomes only; lives in `jira/epics/`.
- **Story** — product language + **acceptance criteria**; QA tests here; **Handoff QA** (Dev fills before Phase 4); **Definition of Done** checklist.
- **Task** — **Done when** for Dev self-check; roll path/data into Story Handoff when story is ready.
- Only **`IN_PROGRESS`** epics get story files + tasks — see `templates/references/epic-status.md`.

## Skills

| Skill | When |
|-------|------|
| `/aaa-pm-about` | Help |
| `/aaa-pm-setup` | Scaffold `docs/pm/` + `docs/qa/ACCESS.md` |
| `/aaa-pm-plan` | Epics + stories + tasks |
| `/aaa-pm-push` | Jira create (delta) |
| `/aaa-pm-intake` | CEO/client feedback |
| `/aaa-pm-sync` | Jira status → task folders |
| `/aaa-pm-task-doing` | One issue → dev context |

**PO workflow:** setup → plan → push · intake · sync (see **PROPOSAL.md** § Bonus).

Independent of app-specific skills (`docs/qa/` test packs, etc.).
