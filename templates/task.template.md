# Task template (planning scratchpad)

Use while **`/aaa-pm-intake`** or when the user/Dev breaks a story into implementation work. **Not** created by default during **`/aaa-pm-plan`**.

The **source of truth** for execution is the markdown file under `docs/pm/jira/tasks/todo/` — copy this structure into **`task-file.template.md`**.

One task ≈ **0.5–2 days** of focused work. Do not auto-generate a batch of sub-tasks under one story — PO/Dev adds tasks when work starts.

---

## Scratchpad format

```text
ID: T-01
Story: S-01
Epic: E-01
Type: FEAT | BUG | CHORE | SPIKE | CHANGE
Priority: Must | Should | Could

Title: <verb> <object> — <outcome in a few words>

Context:
  <Why this task exists — 1–2 sentences linking to story and epic. New reader should understand without opening Jira.>

What to build:
  <Concrete deliverable — screens, endpoints, scripts, config keys. This is where technical detail belongs.>

Acceptance:
  - <Given/When/Then or bullet — each line testable by QA or dev>
  - <Another criterion>
  - <Edge case or error behavior>

Out of scope (this task):
  - <What we are NOT doing in this ticket>

Dependencies:
  - <Blocked by T-02, needs env X, needs design, etc. — or "None">

Files hint:
  - <path/area in repo — optional but saves time>

Estimate: <optional — e.g. 1d>
```

---

## Type → Jira issue type

| Type | Typical Jira type | When to use |
|------|-------------------|-------------|
| FEAT | Story or Task | New behavior |
| BUG | Bug | Broken vs agreed behavior |
| CHANGE | Story / Task | Requirement shift on existing area |
| CHORE | Task | CI, docs, refactor, deps |
| SPIKE | Task | Time-boxed research |

---

## Next step

Create **`docs/pm/jira/tasks/todo/T-01-<kebab-title>.md`** using the full **`task-file.template.md`** (frontmatter + sections for push).
