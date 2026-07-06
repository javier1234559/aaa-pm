# Stories

One markdown file per story: **`S-NN-kebab-title.md`** (e.g. `S-01-case-list-filter.md`).

**Folder = status** (same pattern as tasks):

| Folder | Meaning |
|--------|---------|
| `todo/` | Not started / backlog |
| `inprogress/` | Being implemented |
| `done/` | Shipped |

- **Body** = full Jira Story description (same content in repo and Jira).
- Link from `../OVERVIEW.md` § Stories table.
- Stories belong to epics in `jira/epics/inprogress/` (or `done/` for history).
- **Acceptance criteria** — QA tests in Phase 4.
- **Handoff QA** — Dev fills before QA; leave empty at plan time.
- **Definition of Done** — QA ticks when story is ship-ready.

Template: pack `templates/story.template.md` · copy from `_template.md`.

Format: `templates/references/jira-story-file.md`
