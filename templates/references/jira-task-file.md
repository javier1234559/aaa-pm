# Task file format (`docs/pm/jira/tasks/...`)

**Authoring template:** `templates/task-file.template.md` (full sections — Context, What to build, Acceptance, Jira description).

**Filename:** `T-NN-kebab-title.md` — stable when moving between folders.

| Folder | Meaning |
|--------|---------|
| `tasks/todo/` | Not started / Jira To Do |
| `tasks/inprogress/` | In flight / Jira In Progress |
| `tasks/done/` | Complete / Jira Done |

## Minimum quality bar

A task file is **ready for push** when a new reader can answer:

1. **Why** — ## Context  
2. **What** — ## What to build  
3. **Done when** — ## Acceptance criteria (testable bullets)  
4. **Not doing** — ## Out of scope (this task)

## Push

- **`/aaa-pm-push`** copies **## Jira description** into the Jira issue body (or merges Context + Acceptance if that section is empty).
- Fill frontmatter `jira:` after create.

## Sync

- Match on `jira:` key, else `Local ID: T-XX` in Jira description.
- Move file between `todo` / `inprogress` / `done` — do not rename.

## Types

BUG→Bug; FEAT/CHANGE→Story or Task; CHORE/SPIKE→Task.
