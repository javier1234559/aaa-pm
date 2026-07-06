# Epic template

Use when **`/aaa-pm-plan`** defines or refreshes work.

**Path:** `docs/pm/jira/epics/{todo|inprogress|done}/E-NN-kebab-title.md`  
**Index:** summary row in `docs/pm/jira/OVERVIEW.md` § Epics (link to file).

| Folder | When |
|--------|------|
| `epics/todo/` | Queued epic |
| `epics/inprogress/` | Active epic (default: one at a time) |
| `epics/done/` | Shipped epic |

One epic ≈ one Jira Epic (1–2 weeks solo). **File body = Jira Epic description** — no separate paste block.

---

## OVERVIEW table row

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|
| E-01 | Short verb-led title | IN_PROGRESS | [E-01-….md](./epics/inprogress/E-01-….md) | |

**Status:** `TODO` | `IN_PROGRESS` | `DONE`

---

## File content (`jira/epics/inprogress/E-01-….md`)

```markdown
---
id: E-01
status: IN_PROGRESS
jira:
linked_feature: F-01
---

# Epic — [E-01] [Short verb-led title]

**Status:** IN_PROGRESS  
**Jira:** 

## Why
[2–3 sentences]

## Who cares

## In scope (outcomes)
- 

## Out of scope
- 

## Success looks like

## Timeline (estimate)

## Risks / dependencies
- None
```

---

## Writing tips

- Verb-led title · outcomes in **In scope** · clear **Out of scope**
- Each **In scope** bullet → **one Story file** in `jira/stories/todo/` (split; do not merge into one gate story)
- Only `inprogress/` epics get stories — `references/epic-status.md`, `references/plan-story-first.md`
- Task files come later when Dev starts — not during `/aaa-pm-plan` unless user asks

## Review

- [ ] Title readable on Jira board?
- [ ] In scope enough to split into stories without inventing scope?
- [ ] **Why** and **Success** clear for CEO/QA?
