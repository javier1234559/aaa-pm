# Story file format (`docs/pm/jira/stories/...`)

**Authoring template:** `templates/jira/stories/_template.md`

**Filename:** `S-NN-kebab-title.md` — stable when moving between folders.

| Folder | Meaning |
|--------|---------|
| `stories/todo/` | Not started / backlog |
| `stories/inprogress/` | Being implemented |
| `stories/done/` | Shipped — QA signed off |

## Minimum quality bar

1. **User story** — who wants what and why
2. **Acceptance criteria** — 3–6 testable bullets (QA tests here)
3. **Handoff QA** — Dev fills before QA; empty at plan time
4. **Definition of Done** — QA ticks at end of Phase 4

**QA tests the Story** — not individual Tasks.

## Push

- **`/aaa-pm-push`** copies full file body into Jira Story description.
- Include `Local ID: S-XX` in body for sync.
- Fill frontmatter `jira:` after create.

## Sync

- Match on `jira:` key, else `Local ID: S-XX` in Jira description.
- Move file between `todo` / `inprogress` / `done` — do not rename.
- Refresh OVERVIEW § Stories table File column path.

## Tasks

- Task files live under `jira/tasks/{todo,inprogress,done}/`.
- Add tasks with **`/aaa-pm-task-add`** when implementation reveals more work — no full re-plan needed.

## Legacy flat layout

If stories sit directly in `jira/stories/*.md` (no subfolders), run migration per `templates/references/migrate-epic-story-folders.md`.
