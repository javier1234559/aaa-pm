# Migrate epic/story files to status folders

For product repos created before epic/story `todo|inprogress|done` folders.

## Detect legacy layout

Legacy if any of:

- `docs/pm/jira/epics/E-*.md` (file directly under `epics/`, not in subfolder)
- `docs/pm/jira/stories/S-*.md` (file directly under `stories/`, not in subfolder)

## Scaffold folders

Ensure these exist (copy READMEs from pack `templates/jira/epics/` and `templates/jira/stories/`):

```
docs/pm/jira/epics/{todo,inprogress,done}/
docs/pm/jira/stories/{todo,inprogress,done}/
```

## Move epics

Read each `docs/pm/jira/epics/E-*.md` (flat only):

| Frontmatter `status` or OVERVIEW § Epics | Destination |
|------------------------------------------|-------------|
| `TODO` | `epics/todo/` |
| `IN_PROGRESS` | `epics/inprogress/` |
| `DONE` | `epics/done/` |

Use **move** — same filename. Update OVERVIEW File column links.

## Move stories

For each flat `docs/pm/jira/stories/S-*.md`:

| Signal | Destination |
|--------|-------------|
| Parent epic in `epics/done/` | `stories/done/` |
| Jira status Done (if synced) | `stories/done/` |
| Jira status In Progress | `stories/inprogress/` |
| Default / To Do / not started | `stories/todo/` |

If unsure → `stories/todo/`. User can fix after **`/aaa-pm-sync`**.

## After migration

1. Refresh OVERVIEW epic board + story board counts.
2. Append note to `docs/pm/plan/CHANGELOG.md`.
3. Run **`/aaa-pm-sync`** to align with Jira.

Do **not** delete `_template.md` or README at `epics/` / `stories/` root.
