---
name: aaa-pm-task-start
description: >-
  Pick a task by ID or name, move to inprogress, load story/epic context, and explain how to
  implement — wait for user approval before coding. Use when user says which task to work on.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — task start

Pick up one task, move it to **in progress**, and present an implementation plan for review.

## Gate

Read `templates/references/gate.md`.

## Input

User says which task — any of:

- Local ID: `T-15`, `t15`
- Partial title: "revenue monthly", "comments persist"
- Jira key or URL: `AAAP-43` (fallback — also loads from Jira MCP)

If ambiguous → list matches from `tasks/{todo,inprogress,done}/` and ask user to pick.

## Steps

### 1. Find the task

Search `docs/pm/jira/tasks/{todo,inprogress,done}/**/*.md`:

- Match frontmatter `id:` (e.g. `T-15`)
- Match filename or heading title (case-insensitive, partial OK)
- Match frontmatter `jira:` key if user pasted Jira URL/key

If not found → suggest **`/aaa-pm-sync`** (dev 2 may have created on Jira) or **`/aaa-pm-task-add`**.

### 2. Move to in progress

- If file is in `tasks/todo/` → **move** to `tasks/inprogress/` (same filename).
- If already in `inprogress/` → continue.
- If in `done/` → ask user to confirm reopening; if yes, move to `inprogress/`.
- Update OVERVIEW **Task board** counts.

### 3. Activate parent story (if needed)

From task frontmatter `story` / `epic`:

- If parent story is in `stories/todo/` → move to `stories/inprogress/`.
- Read `docs/pm/jira/stories/{todo,inprogress,done}/S-NN-*.md` — acceptance criteria, Handoff QA.
- Read `docs/pm/jira/epics/{todo,inprogress,done}/E-NN-*.md` — epic scope if needed.
- Update OVERVIEW **Story board** counts if moved.

### 4. Load context

1. Read `docs/pm/project-brief/OVERVIEW.md` (Goal, relevant Feature).
2. Read `docs/pm/jira/OVERVIEW.md`.
3. **Atlassian MCP** (if task has `jira:` key): fetch issue status — read schemas first.
4. Write **`.cursor/context/<TASK-ID>.md`** (e.g. `.cursor/context/T-15.md`):

```markdown
# T-15 — <title>

**Status:** in progress | **Story:** S-XX | **Epic:** E-XX
**Local task:** docs/pm/jira/tasks/inprogress/<filename>.md
**Story:** docs/pm/jira/stories/inprogress/<story-file>.md

## From project brief
- Goal: …
- Feature: F-XX — …

## Task
- Done when: (from task file)

## Parent story (QA tests here)
- Acceptance criteria: …

## Suggested approach
1. …
2. …
3. …

## Files / areas likely touched
- …

## Risks / questions
- …
```

### 5. Present plan in chat (do not implement yet)

Show:

1. **Task** — ID, title, Done when bullets
2. **Story context** — which AC this task supports
3. **Suggested approach** — numbered steps, files to touch, order of work
4. **Open questions** — anything unclear before coding

End with:

> Review this plan. Reply **approve** to start implementation, or give feedback to adjust.

## Rules

- **Do not write code** until user explicitly approves (says approve, ok, làm đi, go ahead, etc.).
- **Do not** transition Jira unless user asks (use **`/aaa-pm-sync`** or approve + implement session).
- If no local task file → offer **`/aaa-pm-task-add`** from story context.
- After approval → user continues in same chat or new chat with repo implementation skill + `.cursor/context/T-XX.md`.

## After approval

> Implement per plan. When done and reviewed → **`/aaa-pm-task-done`**.
