---
name: aaa-pm-task-add
description: >-
  Add new task files to a story when implementation reveals more work — no full re-plan needed.
  Use when user discovers extra tasks while building a story.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — task add

Add one or more task files when work during implementation is larger than the original plan.

## Gate

Read `templates/references/gate.md`.

Read **`templates/task-file.template.md`**, **`templates/references/jira-task-file.md`**.

## Input

User describes new work — any of:

- Story ID + what to add: "S-03 needs tasks for API error handling and retry UI"
- While doing a task: "T-05 revealed we also need T-XX for migration script"
- Paste of discovered work items

## Steps

### 1. Resolve parent story

Find story in `docs/pm/jira/stories/{todo,inprogress,done}/`:

- From user input (`S-03`)
- From current task frontmatter if user references in-progress work
- From `.cursor/context/T-XX.md` if active

Read story file — acceptance criteria, what's already covered by existing tasks.

### 2. Resolve epic

From story frontmatter `epic:` → read epic file in `epics/{folder}/`.

### 3. Allocate IDs

Scan all `tasks/{todo,inprogress,done}/T-*.md` for highest `T-NN`. Next ID = max + 1.

### 4. Draft task files

For each new task, create `docs/pm/jira/tasks/todo/T-NN-kebab-title.md` from `templates/task-file.template.md`:

- `id`, `story`, `epic`, `type`, `priority`, `estimate`
- **Context** — why this emerged (link to parent task if applicable)
- **What to build** — concrete deliverable
- **Done when** — ≥2 testable bullets
- **Out of scope**

Do **not** duplicate work already covered by existing tasks — reference them instead.

### 5. Update OVERVIEW

- Refresh **Task board** todo count.
- Set `jira_pushed: false` on OVERVIEW if new tasks lack `jira:` keys.

### 6. Append changelog

Add row to `docs/pm/plan/CHANGELOG.md`:

```text
YYYY-MM-DD — task-add — S-03 +2 tasks (T-18, T-19) — discovered during T-05
```

### 7. Show summary in chat

Table: new ID | title | story | why added

Ask user to confirm. If they edit → apply changes.

## Rules

- **No full re-plan** — do not rewrite epics/stories unless user asks for **`/aaa-pm-plan`**.
- New tasks always start in `tasks/todo/`.
- Do not create Jira issues here — user runs **`/aaa-pm-push`** (delta).
- If new work is story-sized (new user benefit) → recommend new story via **`/aaa-pm-plan`** or manual story file instead.

## After

> **`/aaa-pm-push`** for new Jira sub-tasks. **`/aaa-pm-task-start T-NN`** to begin.
