# Example — filled Task (planning scratchpad)

See full file: `templates/examples/example-task-file.md` and `aaa-portfolio/jira/tasks/todo/T-15-revenue-monthly-only.md`.

```text
ID: T-01
Story: S-01
Epic: E-01
Type: FEAT
Priority: Must

Title: Add comment persistence — reload shows saved comments

Context:
  Story S-01 requires comments to survive a full page reload. Without storage and GET API,
  the epic cannot meet "persist after every page load."

What to build:
  Server route to append and list comments by client slug; wire client detail to load on mount and POST on submit.

Acceptance:
  - Given a valid client slug, when user POSTs a comment, then it returns 201 and appears in GET list
  - Given existing comments, when user hard-refreshes the page, then the same rows render
  - Given unknown slug, when user POSTs, then 404 with clear error (no silent fail)

Out of scope (this task):
  - Slack notify (T-02)
  - Rich text or attachments

Dependencies:
  - Decision on DB vs GitHub API for persistence (see brief §Technical context)

Files hint:
  - src/app/api/portfolio/comments/route.ts
  - client detail comment list component

Estimate: 1d
```

**Review:** Context + 3 acceptance lines + out of scope — ready to copy into `task-file.template.md`.
