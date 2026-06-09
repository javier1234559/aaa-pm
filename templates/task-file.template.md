# Task file template

**Path:** `docs/pm/jira/tasks/todo/T-NN-kebab-title.md`  
**Moves:** `todo/` → `inprogress/` → `done/` (`/aaa-pm-sync` or manual). **Do not rename** when moving.

**File body (below frontmatter) = Jira Task description** — no separate `## Jira description` section.

Full rules: `templates/references/jira-task-file.md`

---

## File content

```markdown
---
id: T-01
story: S-01
epic: E-01
type: FEAT
jira:
priority: Must
estimate: 1d
---

# [Verb + concrete deliverable]

**Story:** S-01 — [story summary]  
**Epic:** E-01 — [epic title]  
**Type:** FEAT | BUG | CHORE  
**Priority:** Must | Should | Could  
**Estimate:** 1d  
**Jira:** 

## Context

## What to build

## Done when
<!-- Dev self-check before story goes to QA. Roll path + data into Story Handoff QA when ready. -->
-

## Out of scope
-

## Dependencies
None
```

---

## Frontmatter

| Field | Required |
|-------|----------|
| `id` | `T-01` |
| `story` | `S-XX` |
| `epic` | `E-XX` |
| `type` | FEAT, BUG, CHORE, SPIKE, CHANGE |
| `jira` | After push |
| `priority` | Must / Should / Could |
| `estimate` | Optional |

## Review before push

- [ ] **Context** + **Done when** (≥2 testable lines) + **Out of scope**
- [ ] Dev will update parent Story **Handoff QA** when story is ready for QA
