---
name: aaa-pm-intake
description: >-
  Process pasted feedback — save raw-intake file, update intake index, project-brief, and/or
  jira task files. Use when user pastes CEO/client/QA feedback or says intake.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — intake

## Gate

Read `templates/references/gate.md`.

## Expected input

```text
Source: CEO | Client | QA | Other
---
<paste here>
```

Infer source if missing.

## Process

1. Read `docs/pm/project-brief/OVERVIEW.md`.
2. Create **`docs/pm/intake/raw-intake/YYYY-MM-DD-<source>-<short-topic>.md`** (verbatim paste + frontmatter from `templates/intake/raw-intake/_template.md`).
3. Split into discrete items; classify per `templates/references/intake-types.md`.
4. Per item:
   - **Small** → new task file in `docs/pm/jira/tasks/todo/` under active epic; update stories table if new story; set `jira_pushed: false` on jira OVERVIEW if new work
   - **QUESTION** → §Open questions row on brief
   - **Large CHANGE** → patch §Features / §Scope / §Decision log on brief; recommend **`/aaa-pm-plan`**
5. Append row to **`docs/pm/intake/OVERVIEW.md`** (link to raw file).
6. Set `processed: true` on raw file when done.
7. Output table: item → type → action → next step.

## Jira

- Do not call Jira unless user says "intake and push".
- Then → **`/aaa-pm-push`** after files updated.

## Re-plan

Recommend **`/aaa-pm-plan`** when intake changes §Goal, Must priorities, §Scope, or new epic theme.
