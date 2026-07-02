# Brief gate (all aaa-pm skills except setup)

Before any work:

1. Read `docs/pm/project-brief/OVERVIEW.md`.
2. If missing → stop: run **`/aaa-pm-setup`**.
3. If frontmatter `brief_status` is not `complete` → stop: run **`/aaa-pm-setup`**.
4. For **push**: require `docs/pm/jira/OVERVIEW.md` with at least one epic or story needing keys (task files optional); user must confirm push in session.
5. For **plan**: `brief_status: complete` only (may create empty `jira/` on first plan).

**Jira key:** read `jira_project_key` from `project-brief/OVERVIEW.md` frontmatter (or `docs/pm/jira/OVERVIEW.md` if duplicated there).
