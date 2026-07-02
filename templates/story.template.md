# Story template

Use when **`/aaa-pm-plan`** breaks an **active** epic into stories.

**Path:** `docs/pm/jira/stories/S-NN-kebab-title.md`  
**Index:** row in `docs/pm/jira/OVERVIEW.md` § Active stories (link to file).

**File body = Jira Story description** — no separate paste block.

Stories are **product language only**. **QA tests acceptance criteria** on the Story — not individual Tasks.

---

## OVERVIEW table row

| ID | Epic | Story | Priority | File | Jira |
|----|------|-------|----------|------|------|
| S-01 | E-01 | One sentence user benefit | Must | [S-01-….md](./stories/S-01-….md) | |

**Good story line:** *Staff view the case list and filter by application type.*

**Avoid:** POST `/api/…`, framework names → **tasks** only.

---

## File content (`jira/stories/S-01-….md`)

```markdown
---
id: S-01
epic: E-01
priority: Must
jira:
---

# Story — [S-01] [One sentence — user benefit]

**Epic:** E-01 — [epic title]  
**Priority:** Must  
**Jira:** 

## Summary

## User story
As a [role], I want [capability], so that [benefit].

## From Epic
-

## Acceptance criteria
-

## Not in this story
-

## Priority rationale

## Handoff QA

Project test access: `docs/qa/ACCESS.md`

- **Path:** 
- **Data for this story:** 
- **Notes:** 

## Definition of Done

- [ ] All acceptance criteria pass on staging
- [ ] Handoff QA filled — path and data verified
- [ ] No open Blocker or Critical bugs linked to this story
- [ ] Feature visible on staging matches what Dev demoed
- [ ] Regression: related flows still work (or "N/A" with reason)
```

---

## Rules

| Rule | Detail |
|------|--------|
| Derive from epic | Every story maps to an epic **In scope** bullet — prefer **one bullet → one story** |
| Story size | One user benefit; 3–6 AC; split instead of one story + many tasks underneath |
| Acceptance criteria on Story | QA Phase 4 — 3–6 testable bullets |
| Handoff QA | Dev fills before QA; empty at plan time |
| Definition of Done | Same checklist every story; QA ticks last |
| No tech in story | APIs, routes, files → **task** files (added later by Dev) |
| Tasks at plan time | **Do not** create task files during `/aaa-pm-plan` unless user asks |

## Review

- [ ] Client/CEO understands without reading code?
- [ ] Acceptance criteria testable?
- [ ] **Not in this story** prevents overlap?
