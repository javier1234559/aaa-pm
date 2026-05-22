---
name: aaa-pm-plan
description: >-
  Break down project brief into epics (jira/OVERVIEW), active stories, and task files in
  jira/tasks/todo/. Appends plan/CHANGELOG. Use for plan, breakdown, epics, re-plan.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — plan

## Gate

Read `templates/references/gate.md` — `brief_status: complete` required.

Read **`templates/references/epic-status.md`** and **`templates/references/jira-task-file.md`**.

## Templates

- `templates/epic.template.md`
- `templates/story.template.md`
- `templates/task-file.template.md`
- `templates/examples/example-jira-overview.md`
- `templates/examples/example-task-file.md`

## Process

1. Read `docs/pm/project-brief/OVERVIEW.md` (§Goal, §Features, §Scope).
2. Ensure `docs/pm/jira/OVERVIEW.md` exists (empty scaffold OK).
3. Draft **all epics** in ## Epics table (`TODO` | `IN_PROGRESS` | `DONE`).
4. Set `active_epics` in jira frontmatter (default **one** `IN_PROGRESS`; multiple only if user confirms).
5. For **active epic(s) only**: use **`templates/epic.template.md`** — epics table + **`## Epic detail — E-XX`** blocks (Why, In scope, Success, Jira description).
6. Use **`templates/story.template.md`** — stories table + **`## Story detail — S-XX`** per story (user story, done when, Jira description).
7. For each story: create **`docs/pm/jira/tasks/todo/T-NN-kebab-title.md`** using **`task-file.template.md`** — fill Context, What to build, Acceptance, Out of scope, Jira description (not a one-line stub).
8. **Do not** add stories, detail blocks, or task files for `TODO` / `DONE` epics.
9. When switching epic: mark old `DONE`, remove its story rows and detail blocks, move/create task files for new epic; leave old task files in `done/` if already shipped.
10. Update **Task board** counts in `jira/OVERVIEW.md` (file counts in todo/inprogress/done).
11. Show tree in chat; user approves.
12. Bump `plan_version` on `jira/OVERVIEW.md` and `docs/pm/plan/CHANGELOG.md`; set `jira_pushed: false` if new/changed tasks without keys.

## Rules

- Stories: product language only — no tech (see `story.template.md`).
- Tasks: technical detail in **task files** only.
- Do not create Jira issues in this skill.

## After

> **`/aaa-pm-push`** when ready. **`/aaa-pm-sync`** after manual Jira edits.
