# Epic file format (`docs/pm/jira/epics/...`)

**Authoring template:** `templates/jira/epics/_template.md`

**Filename:** `E-NN-kebab-title.md` — stable when moving between folders.

| Folder | Meaning | OVERVIEW status |
|--------|---------|-----------------|
| `epics/todo/` | Queued | `TODO` |
| `epics/inprogress/` | Active | `IN_PROGRESS` |
| `epics/done/` | Shipped | `DONE` |

**Folder = status.** OVERVIEW § Epics table and frontmatter `active_epics` must match folder location.

## Minimum quality bar

1. **Why** — client problem, why this chunk is one epic
2. **In scope** — user-visible outcomes (each bullet → one Story)
3. **Out of scope** — at least one real exclusion
4. **Success looks like** — outcome when done, not "all tickets closed"

## Push

- **`/aaa-pm-push`** copies full file body into Jira Epic description.
- Include `Local ID: E-XX` in body for sync.
- Fill frontmatter `jira:` after create.

## Sync

- Match on `jira:` key, else `Local ID: E-XX` in Jira description.
- Move file between `todo` / `inprogress` / `done` — do not rename.
- Update OVERVIEW § Epics status column and `active_epics` when moving to/from `inprogress/`.

## Legacy flat layout

If epics sit directly in `jira/epics/*.md` (no subfolders), run migration per `templates/references/migrate-epic-story-folders.md`.
