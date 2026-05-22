# Migrate `PROJECT_BRIEF.md` → `docs/pm/`

Run during **`/aaa-pm-setup`** when repo root still has `PROJECT_BRIEF.md`.

## Split map

| Legacy section | Destination |
|----------------|-------------|
| Frontmatter + §One-liner … §Decision log | `docs/pm/project-brief/OVERVIEW.md` |
| §Delivery plan ### Epics | `docs/pm/jira/OVERVIEW.md` ### Epics |
| §Delivery plan ### Stories | `docs/pm/jira/OVERVIEW.md` ### Stories |
| §Delivery plan ### Tasks | One file per row → `docs/pm/jira/tasks/todo/` or `done/` if Jira status known |
| §Plan history | `docs/pm/plan/CHANGELOG.md` |
| §Intake log | `docs/pm/intake/OVERVIEW.md` rows + optional `raw-intake/` stubs |

## Task file from table row

Row: `| T-01 | S-01 | Title text | FEAT | AAAP-3 |`

- Create `docs/pm/jira/tasks/todo/T-01-<slug>.md` (or `done/` if synced Done).
- Frontmatter: `id`, `story`, `epic` from row; `jira: AAAP-3` if present; `type: FEAT`.
- Body: title + acceptance placeholder if none in table.

## Frontmatter on `jira/OVERVIEW.md`

```yaml
jira_project_key: <from brief>
plan_version: <from brief plan_version>
jira_pushed: <from brief>
active_epics: [E-04]   # all IN_PROGRESS epics
last_synced_at: null
```

## After migrate

- Replace root `PROJECT_BRIEF.md` with stub pointing to `docs/pm/project-brief/OVERVIEW.md` (optional, user may delete).
- Do not duplicate delivery tables at root.
