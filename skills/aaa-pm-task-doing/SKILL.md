---
name: aaa-pm-task-doing
description: >-
  Load Jira issue from URL/key; match docs/pm/jira task file; write .cursor/context/<KEY>.md
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
2. Find local task: search `docs/pm/jira/tasks/{todo,inprogress,done}/` for matching `jira:` in frontmatter or grep key in file body.
3. Read `docs/pm/jira/OVERVIEW.md` for epic/story row if linked.
4. **Atlassian MCP**: fetch issue (summary, description, status, type, parent). Read schemas first.
5. Write **`.cursor/context/<KEY>.md`**:

```markdown
# <KEY> — <summary>

**Status:** <jira> | **Type:** <type> | **Parent:** <parent>
**Local task:** docs/pm/jira/tasks/<folder>/<filename>.md

## From project brief
- Goal: …
- Feature: F-XX — …

## Local task
- ID: T-XX | Story: S-XX | Epic: E-XX
- Acceptance: (from task file)

## Jira description
<verbatim or structured>

## Technical context
- From brief §Technical context
- **Likely files:** (from task ## Files hint + repo)

## Out of scope
- From brief §Scope Out

## Suggested next steps
1. …
```

6. Tell user:

> Context: `.cursor/context/<KEY>.md` — new chat + repo implementation skill.

## Rules

- Do not implement code unless user asks.
- Do not transition Jira unless user asks.
- If no local task file → still write context from Jira + brief; note "no local task file".
