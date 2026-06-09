# Example — full task file

Path: `docs/pm/jira/tasks/todo/T-01-comment-persistence.md`

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

# Add comment persistence — reload shows saved comments

**Story:** S-01 — Users still see their comments after refreshing the page  
**Epic:** E-01 — Support comments on client records and Slack notify  
**Type:** FEAT  
**Priority:** Must  
**Estimate:** 1d  
**Jira:** 

## Context

Foundation for S-01: without durable storage and a read API, reload wipes user trust.

**Feature link (brief):** F-03 — Internal comments API  
**Local ID:** T-01

## What to build

- `POST` and `GET` handlers for comments scoped by client slug
- Client detail: load thread on mount; submit form appends and refreshes list
- Validate slug exists before accept POST

## Done when

- POST valid slug → 201 and comment appears in GET for that slug
- Hard refresh → same comments render in order
- Unknown slug POST → 404 with JSON error (no 500 in UI)

## Out of scope (this task)

- Slack webhook on create (T-02)
- Styling pass beyond basic list + form

## Dependencies

- Persistence layer agreed (DB or GitHub API)
```

Full file body (from `# Title` through sections) = Jira Task description. When story is ready for QA, Dev fills **Handoff QA** on `stories/S-01-*.md`. After push: set `jira: PORT-42`. `/aaa-pm-sync` moves file when Done on board.
