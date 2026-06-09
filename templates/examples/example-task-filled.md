# Example — filled Task (planning scratchpad)

See full file: `templates/examples/example-task-file.md`.

```text
ID: T-01
Story: S-01
Epic: E-01
Type: FEAT
Priority: Must

Title: Add comment persistence — reload shows saved comments

Context:
  Foundation for S-01 — need POST+GET by client slug.

What to build:
  API routes + client detail load/submit.

Done when:
  - POST valid → 201 + in GET list
  - Refresh → same comments visible
  - Unknown slug → 404

Out of scope:
  - Slack (T-02)

Estimate: 1d
```

QA tests the **Story** acceptance criteria. Dev rolls path/data into Story **Handoff QA** when ready.
