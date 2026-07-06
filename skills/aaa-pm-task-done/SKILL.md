---
name: aaa-pm-task-done
description: >-
  Mark a task as done after user review — move file to done/, update board counts, optionally
  transition Jira. Use when user approves completed work on a task.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — task done

Close out a task after the user confirms the work is acceptable.

## Gate

Read `templates/references/gate.md`.

## Input

User confirms task is done — any of:

- Local ID: `T-15`
- "mark current task done", "task done", "xong T-15"
- Reference to task in `tasks/inprogress/`

If ambiguous → list tasks in `tasks/inprogress/` and ask.

## Preconditions

- User has reviewed the implementation (in this or a prior session).
- Accept signals: "done", "approve", "ok", "xong", "looks good", "ship it".

If user reports issues → do **not** mark done; suggest fixes or **`/aaa-pm-task-start`** to replan.

## Steps

### 1. Find task

Search `docs/pm/jira/tasks/inprogress/` (also check `todo/` if user skipped start).

Match by ID, title, or context file `.cursor/context/T-XX.md`.

### 2. Move to done

- **Move** file from `inprogress/` → `done/` (same filename).
- Update OVERVIEW **Task board** counts.

### 3. Check parent story

Read parent story from `docs/pm/jira/stories/{todo,inprogress,done}/`.

- If **all tasks** for this story are in `tasks/done/` (or user confirms story complete):
  - Ask: move story to `stories/done/`?
  - If yes → move story file, update **Story board** counts.
  - Remind Dev to fill **Handoff QA** on story if ready for QA.

### 4. Jira (optional)

If task frontmatter has `jira:` key **and** user says "sync jira" or "update jira":

1. Read Atlassian MCP schemas.
2. Transition issue to Done.
3. Suggest **`/aaa-pm-sync`** to reconcile all folders.

Otherwise → suggest **`/aaa-pm-sync`** on next scheduled sync.

### 5. Context cleanup

- Update `.cursor/context/T-XX.md` header: `**Status:** done`
- Or note user can delete context file.

## Report in chat

```text
✓ T-15 moved to tasks/done/
  Story S-03: 2/3 tasks done (T-16 still in progress)
  Next: /aaa-pm-task-start T-16  or  /aaa-pm-sync
```

## Rules

- Do not mark done without explicit user approval in this session.
- Do not delete task files — only move to `done/`.
- Do not auto-close Jira unless user asks.

## After

> Pick next task: **`/aaa-pm-task-start`**. New work discovered → **`/aaa-pm-task-add`**.
