---
name: aaa-pm-plan
description: >-
  Break down project brief into epic files, story files, task files, and jira/OVERVIEW index.
  Appends plan/CHANGELOG. Use for plan, breakdown, epics, re-plan.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — plan

## Gate

Read `templates/references/gate.md` — `brief_status: complete` required.

Read **`templates/references/epic-status.md`**, **`templates/references/jira-task-file.md`**, **`PROPOSAL.md`** at pack root (ticket templates).

## Templates

- `templates/epic.template.md` → `docs/pm/jira/epics/E-NN-*.md`
- `templates/story.template.md` → `docs/pm/jira/stories/S-NN-*.md`
- `templates/task-file.template.md` → `docs/pm/jira/tasks/todo/T-NN-*.md`
- `templates/examples/` (pack-only)

## Process

1. Read `docs/pm/project-brief/OVERVIEW.md` (§Goal, §Features, §Scope).
2. Ensure `docs/pm/jira/OVERVIEW.md`, `jira/epics/`, `jira/stories/` exist (setup scaffold).
3. Ensure `docs/qa/ACCESS.md` exists (placeholder OK — fill staging/login at Phase 2).
4. Draft **all epics**: one file per epic in `jira/epics/` + rows in OVERVIEW § Epics (`TODO` | `IN_PROGRESS` | `DONE`).
5. Set `active_epics` in OVERVIEW frontmatter (default **one** `IN_PROGRESS`).
6. For **active epic(s) only**: one story file per story in `jira/stories/` + OVERVIEW § Active stories.
   - Fill acceptance criteria; leave **Handoff QA** bullets empty; **Definition of Done** unchecked.
7. For each active story: create `jira/tasks/todo/T-NN-*.md` — Context, What to build, **Done when**, Out of scope (not stubs).
8. **Do not** add story files or tasks for `TODO` / `DONE` epics.
9. When switching epic: old → `DONE`, archive/remove its active story rows; new → `IN_PROGRESS`, new story + task files.
10. Update **Task board** counts on OVERVIEW.
11. Show tree in chat; user approves.
12. Bump `plan_version` on OVERVIEW and `docs/pm/plan/CHANGELOG.md`; set `jira_pushed: false` if new/changed items lack keys.

## Rules

- **Local file body = Jira description** — no fenced "paste on push" blocks.
- Stories: product language; **acceptance criteria on Story** (QA tests here).
- Tasks: technical detail; **Done when** for Dev; Handoff on Story when ready for QA.
- Do not create Jira issues in this skill.

## After

> **`/aaa-pm-push`** when ready. **`/aaa-pm-sync`** after manual Jira edits.
