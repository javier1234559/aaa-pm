# Task file format (`docs/pm/jira/tasks/...`)

**Authoring template:** `templates/task-file.template.md`

**Filename:** `T-NN-kebab-title.md` — stable when moving between folders.

| Folder | Meaning |
|--------|---------|
| `tasks/todo/` | Not started / Jira To Do |
| `tasks/inprogress/` | In flight / Jira In Progress |
| `tasks/done/` | Complete / Jira Done |

## Minimum quality bar

1. **Why** — ## Context  
2. **What** — ## What to build  
3. **Done when** — testable bullets (Dev self-check)  
4. **Not doing** — ## Out of scope  

**QA tests the parent Story** (acceptance criteria + Handoff QA + DoD) — not each Task.

When the story is ready for QA, Dev fills **Handoff QA** on `jira/stories/{todo,inprogress,done}/S-XX-*.md` (path + data).

## Push

- **`/aaa-pm-push`** copies the **full task file body** (from `# Title` through sections) into Jira — no separate Jira description block.
- Include `Local ID: T-XX` in **Context** or after frontmatter fields in body for sync.
- Fill frontmatter `jira:` after create.

## Sync

- Match on `jira:` key, else `Local ID: T-XX` in Jira description (see `sync-matching.md`).
- Move file between `todo` / `inprogress` / `done` — do not rename.

## Types

BUG→Bug; FEAT/CHANGE→Story or Task; CHORE/SPIKE→Task.
