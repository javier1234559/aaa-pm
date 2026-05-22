# Story template

Use when **`/aaa-pm-plan`** breaks an **active** epic (`IN_PROGRESS`) into stories. Stories are **product language only** — what the user or stakeholder gets, not how we build it.

Write the **one-line summary** in `docs/pm/jira/OVERVIEW.md` § Active stories, plus a **detail block** per story (below the table or under `## Story detail — S-01`).

---

## Quick row (OVERVIEW table)

| Column | What to write |
|--------|----------------|
| **ID** | `S-01`, `S-02`, … |
| **Epic** | Parent `E-01` |
| **Story** | One plain sentence — see examples below |
| **Priority** | `Must` \| `Should` \| `Could` |
| **Jira** | Empty until push |

**Story line examples (good):**

- Users still see their comments after refreshing the page.
- Leadership sees a Sales Pipeline timeline for deals before discovery starts.
- The dashboard shows four phase summary cards: Sales, Discovery, Build, and QA.

**Avoid in the Story column (too technical):**

- POST `/api/comments`, table names, framework names, env var names → put those in **tasks** only.

---

## Detail block (per story)

```markdown
## Story detail — S-01

**Epic:** E-01 — <epic title>

**Summary (same as table row):**  
<One sentence — the story line from the table.>

**User story (optional but helpful for Jira):**  
As a <role>, I want <capability>, so that <benefit>.

**Comes from epic bullet:**  
- <Quote or paraphrase the epic "In scope" bullet this story delivers>

**What "done" means (product level):**  
- <Observable outcome #1 — no implementation detail>
- <Outcome #2 if needed>

**Not in this story:**  
- <Edge case or follow-up explicitly deferred>

**Priority rationale:**  
<One line: why Must vs Should — e.g. "CEO demo blocker" or "nice polish after Gantt ships">

**Jira Story description (paste on push):**  
```
Story: <summary line>
User story: As a ... I want ... so that ...
Done when:
- ...
Epic: E-01
Local ID: S-01
Brief: docs/pm/project-brief/OVERVIEW.md
```
```

---

## Rules

| Rule | Detail |
|------|--------|
| Derive from epic | Every story maps to an epic **In scope** bullet — do not invent scope |
| No tech in story | APIs, routes, DB, files, libraries → **task** files only |
| No task-level AC here | Detailed acceptance criteria live in **tasks** under this story |
| One story ≈ one user outcome | Merge bullets only if inseparable in one release slice |

---

## Review

- [ ] A PM or client could understand the story without reading code?
- [ ] **Done when** is testable in plain language (even if QA writes formal cases later)?
- [ ] **Not in this story** prevents confusion with neighboring stories?
