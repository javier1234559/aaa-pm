---
name: aaa-pm-plan
description: >-
  Break down project brief into epic files and story files (jira/OVERVIEW index).
  Stories first — do not create task/sub-task files unless user asks. Appends plan/CHANGELOG.
  Use for plan, breakdown, epics, re-plan.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — plan

## Gate

Read `templates/references/gate.md` — `brief_status: complete` required.

Read **`templates/references/plan-story-first.md`** (mandatory), **`templates/references/epic-status.md`**, **`templates/references/jira-task-file.md`**, **`PROPOSAL.md`** at pack root (ticket templates).

## Templates

- `templates/epic.template.md` → `docs/pm/jira/epics/E-NN-*.md`
- `templates/story.template.md` → `docs/pm/jira/stories/S-NN-*.md`
- `templates/task-file.template.md` → only when user explicitly asks for tasks
- `templates/examples/` (pack-only)

## Process

1. Read `docs/pm/project-brief/OVERVIEW.md` (§Goal, §Features, §Scope).
2. Ensure `docs/pm/jira/OVERVIEW.md`, `jira/epics/`, `jira/stories/` exist (setup scaffold).
3. Ensure `docs/qa/ACCESS.md` exists (placeholder OK — fill staging/login at Phase 2).
4. Draft **all epics**: one file per epic in `jira/epics/` + rows in OVERVIEW § Epics (`TODO` | `IN_PROGRESS` | `DONE`).
5. Set `active_epics` in OVERVIEW frontmatter (default **one** `IN_PROGRESS`).
6. For **active epic(s) only**: **one story file per user benefit** in `jira/stories/` + OVERVIEW § Active stories.
   - Map each epic **In scope** bullet to its own story when possible — do not merge unrelated outcomes into one story.
   - Fill acceptance criteria (3–6 testable bullets); leave **Handoff QA** empty; **Definition of Done** unchecked.
7. **Do not** create `jira/tasks/todo/T-NN-*.md` during plan unless the user explicitly asks (e.g. "also create tasks", "break into sub-tasks"). Dev/PO adds tasks when implementation starts.
8. **Do not** add story files for `TODO` / `DONE` epics.
9. When switching epic: old → `DONE`, archive/remove its active story rows; new → `IN_PROGRESS`, new story files only (no auto-tasks).
10. Update **Task board** counts on OVERVIEW (0 is OK if no task files).
11. Show tree in chat (epics + stories; mention tasks deferred unless user asked); user approves.
12. Bump `plan_version` on OVERVIEW and `docs/pm/plan/CHANGELOG.md`; set `jira_pushed: false` if new/changed items lack keys.

## Rules

- **Stories first** — see `templates/references/plan-story-first.md`.
- **Local file body = Jira description** — no fenced "paste on push" blocks.
- Stories: product language; **acceptance criteria on Story** (QA tests here).
- Tasks: optional at plan time; technical detail; **Done when** for Dev; Handoff on Story when ready for QA.
- Do not create Jira issues in this skill.

## After

> **`/aaa-pm-push`** when ready (Epics + Stories; Tasks only if files exist). **`/aaa-pm-sync`** after manual Jira edits. Add task files manually or ask the agent to break down a story when Dev starts.
