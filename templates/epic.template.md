# Epic template

Use when **`/aaa-pm-plan`** defines or refreshes work. One epic ≈ one Jira Epic (1–2 weeks solo). Write the **summary row** in `docs/pm/jira/OVERVIEW.md` § Epics, then add a **detail block** below the table (same file) so readers and Jira get full context.

---

## Quick row (OVERVIEW table)

| Column | What to write |
|--------|----------------|
| **ID** | `E-01`, `E-02`, … |
| **Epic** | Short title — verb-led feature name (readable on the board) |
| **Status** | `TODO` \| `IN_PROGRESS` \| `DONE` |
| **Jira** | Empty until `/aaa-pm-push`; then e.g. `AAAP-1` |

---

## Detail block (copy under `## Epic detail — E-01` in `jira/OVERVIEW.md`)

```markdown
## Epic detail — E-01

**Title:** <Same as table — action phrase, e.g. "Enhance Gantt chart UI">

**Linked feature (brief):** F-05 — <one line from project-brief §Features, or "—">

**Why this epic exists:**  
<2–3 sentences. What problem this slice solves and why it is grouped as one epic — not the whole product goal, just this chunk.>

**Who cares:**  
<Role — e.g. CEO sees pipeline timing; engineering ships read-only chart.>

**In scope (outcomes — not tasks):**  
- <User-visible or PM-visible outcome #1 — one idea per bullet>
- <Outcome #2>
- <Outcome #3>

**Out of scope (for this epic):**  
- <Explicit exclusion — prevents scope creep>
- <Another exclusion>

**Success looks like:**  
<One short paragraph: how we know this epic is DONE without listing every ticket.>

**Dependencies / risks:**  
- <Optional: needs API from client, design sign-off, another epic, env secret, etc.>

**Jira Epic description (paste on push):**  
```
Goal: <one line>
In scope:
- ...
Out of scope:
- ...
Success: ...
Feature: F-XX
Local ID: E-01
Brief: docs/pm/project-brief/OVERVIEW.md
```
```

---

## Writing tips

| Do | Avoid |
|----|--------|
| Verb-led title ("Support comments and Slack notify") | Noun-only labels ("Comments API") |
| Outcomes in **In scope** (what changes for the user/PM) | Tasks, file paths, or "implement X API" |
| One atomic idea per bullet | Stacked clauses ("do A and B and C") |
| Clear **Out of scope** | Leaving exclusions implicit |

**Stories:** Each **In scope** bullet usually becomes one **story** (`story.template.md`). Tasks come later under those stories.

**Status:** Only `IN_PROGRESS` epics get story rows and task files — see `references/epic-status.md`.

---

## Review before push

- [ ] Title readable on Jira board without opening the epic?
- [ ] In scope bullets enough to split into stories without inventing new scope?
- [ ] Out of scope lists at least one real exclusion?
- [ ] **Why** and **Success** filled so a new teammate understands the epic in one read?
