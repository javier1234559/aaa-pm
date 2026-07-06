# Epics

One markdown file per epic: **`E-NN-kebab-title.md`** (e.g. `E-01-basic-case-management.md`).

**Folder = status** (same pattern as tasks):

| Folder | Status |
|--------|--------|
| `todo/` | Queued — `TODO` |
| `inprogress/` | Active — `IN_PROGRESS` |
| `done/` | Shipped — `DONE` |

- **Body** = full Jira Epic description (same content in repo and Jira).
- Link from `../OVERVIEW.md` § Epics table.
- Only `inprogress/` epics get active stories in `jira/stories/`.

Template: pack `templates/epic.template.md` · copy from `_template.md` when creating a new epic.

Format: `templates/references/jira-epic-file.md`
