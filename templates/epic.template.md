# Epic template

Use when **`/aaa-pm-plan`** defines or refreshes work.

**Path:** `docs/pm/jira/epics/E-NN-kebab-title.md`  
**Index:** summary row in `docs/pm/jira/OVERVIEW.md` § Epics (link to file).

One epic ≈ one Jira Epic (1–2 weeks solo). **File body = Jira Epic description** — no separate paste block.

---

## OVERVIEW table row

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|
| E-01 | Short verb-led title | IN_PROGRESS | [E-01-….md](./epics/E-01-….md) | |

**Status:** `TODO` | `IN_PROGRESS` | `DONE`

---

## File content (`jira/epics/E-01-….md`)

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
- Each **In scope** bullet → one Story file in `jira/stories/`
- Only `IN_PROGRESS` epics get stories + tasks — `references/epic-status.md`

## Review

- [ ] Title readable on Jira board?
- [ ] In scope enough to split into stories without inventing scope?
- [ ] **Why** and **Success** clear for CEO/QA?
