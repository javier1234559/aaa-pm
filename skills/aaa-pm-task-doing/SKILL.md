---
name: aaa-pm-task-doing
description: >-
  Load Jira issue from URL/key; match docs/pm/jira task/story/epic files; write .cursor/context/<KEY>.md
  for implementation. Use when user pastes Jira link or says task-doing.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — task doing

## Gate

Read `templates/references/gate.md`.

## Input

Jira **URL** or **issue key** (e.g. `AAAP-43`).

## Steps

1. Read `docs/pm/project-brief/OVERVIEW.md` (Goal, relevant Feature).
2. Find local task: `docs/pm/jira/tasks/{todo,inprogress,done}/` — match `jira:` frontmatter or key in body.
3. From task frontmatter `story` / `epic`, read:
   - `docs/pm/jira/stories/S-NN-*.md` — acceptance criteria, Handoff QA (for context)
   - `docs/pm/jira/epics/E-NN-*.md` — epic scope if needed
4. Read `docs/pm/jira/OVERVIEW.md` for board context.
5. **Atlassian MCP**: fetch issue (summary, description, status, type, parent). Read schemas first.
6. Write **`.cursor/context/<KEY>.md`**:

```markdown
# <KEY> — <summary>

**Status:** <jira> | **Type:** <type> | **Parent:** <parent>
**Local task:** docs/pm/jira/tasks/<folder>/<filename>.md
**Story:** docs/pm/jira/stories/<story-file>.md

## From project brief
- Goal: …
- Feature: F-XX — …

## Local task
- ID: T-XX | Story: S-XX | Epic: E-XX
- Done when: (from task file)

## Parent story (QA tests here — Dev self-checks task only)
- Acceptance criteria: (from story file)
- Handoff QA: (from story file if filled)

## Description (from Jira / local file)
<full task body>

## Technical context
- From brief §Technical context

## Out of scope
- Task out of scope + brief §Scope Out

## Suggested next steps
1. …
```

7. Tell user:

> Context: `.cursor/context/<KEY>.md` — new chat + repo implementation skill.

## Rules

- Do not implement code unless user asks.
- Do not transition Jira unless user asks.
- If no local task file → context from Jira + brief; note "no local task file".
- When story is ready for QA, Dev updates **Handoff QA** on the story file.
