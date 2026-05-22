---
name: aaa-pm-setup
description: >-
  Scaffold docs/pm/ in any product repo (project-brief, intake, plan, jira tasks).
  Complete project-brief OVERVIEW until brief_status is complete. Migrate legacy PROJECT_BRIEF.md.
metadata:
  pack: aaa-pm
disable-model-invocation: true
---

# AAA PM — setup

Interactive setup until **`docs/pm/project-brief/OVERVIEW.md`** has `brief_status: complete`.

## Pack root

`{pack-root}/templates/` — see `templates/references/paths.md`.

## Step 0 — Scaffold `docs/pm/`

If `docs/pm/project-brief/OVERVIEW.md` **missing**, copy from pack:

| Pack source | Product destination |
|-------------|---------------------|
| `templates/repo-root/AGENTS.md` | `docs/pm/AGENTS.md` |
| `templates/repo-root/README.md` | `docs/pm/README.md` |
| `templates/project-brief/OVERVIEW.template.md` | `docs/pm/project-brief/OVERVIEW.md` |
| `templates/project-brief/CHANGELOG.template.md` | `docs/pm/project-brief/CHANGELOG.md` |
| `templates/intake/OVERVIEW.template.md` | `docs/pm/intake/OVERVIEW.md` |
| `templates/intake/raw-intake/` | `docs/pm/intake/raw-intake/` (README + `_template.md`) |
| `templates/plan/CHANGELOG.template.md` | `docs/pm/plan/CHANGELOG.md` |
| `templates/jira/OVERVIEW.template.md` | `docs/pm/jira/OVERVIEW.md` |
| `templates/jira/tasks/todo/` | `docs/pm/jira/tasks/todo/` |
| `templates/jira/tasks/inprogress/` | `docs/pm/jira/tasks/inprogress/` |
| `templates/jira/tasks/done/` | `docs/pm/jira/tasks/done/` |

**Do not** copy `templates/examples/` into the product repo.

If scaffold exists → ask: **continue brief**, **merge new input**, or **migrate from root `PROJECT_BRIEF.md`**.

## Step 0b — Migrate legacy `PROJECT_BRIEF.md`

If repo root has `PROJECT_BRIEF.md` and user wants migrate:

1. Read `templates/references/migrate-legacy-brief.md`.
2. Split content into `docs/pm/` per map (brief, jira OVERVIEW, task files, plan CHANGELOG, intake index).
3. Optionally replace root file with `templates/repo-root/PROJECT_BRIEF.stub.md`.

## Step 1 — Gather input

- Paste proposal, transcript, boss message
- Optional: `README.md`, `docs/` product notes

Ask **one section group at a time** when gaps remain.

## Step 2 — Required sections (`project-brief/OVERVIEW.md`)

| Section | Rule |
|---------|------|
| Frontmatter | `slug`, `name`, `phase`, `brief_version`, `updated`, `brief_status` |
| `jira_project_key` | Value or row in §Open questions (Q-jira) |
| §One-liner | ≥1 sentence |
| §Problem, §Goal | Filled |
| §Users | ≥1 row |
| §Features | ≥1 Must (F-01…) |
| §Scope In / Out | Each ≥1 bullet |
| §Technical context, §Constraints | Filled or "None known" |

Optional: §Assumptions, §Assets, §Decision log.

**Do not** fill `jira/OVERVIEW` epics or task files during setup — **`/aaa-pm-plan`** owns that.

## Step 3 — Confirm

Set `brief_status: complete`, bump `updated`, prepend `project-brief/CHANGELOG.md`.

## Step 4 — Handoff

> Brief complete. Next: **`/aaa-pm-plan`** → **`/aaa-pm-push`**. Feedback: **`/aaa-pm-intake`**.

## Rules

- No secrets or pricing tables in git-tracked PM docs.
- Same scaffold works for **any** repo — only brief content is project-specific.
