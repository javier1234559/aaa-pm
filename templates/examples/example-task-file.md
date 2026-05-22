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

## Context

**Story:** S-01 — Users still see their comments after refreshing the page.

**Epic:** E-01 — Support comments on client records and Slack notify

**Why this task:**  
This is the foundation for the epic: without durable storage and a read API, reload wipes user trust. Delivers the first testable slice of S-01 before Slack or polish work.

**Feature link (brief):** F-03 — Internal comments API

## What to build

- `POST` and `GET` handlers for comments scoped by client slug  
- Client detail: load thread on mount; submit form appends and refreshes list  
- Validate slug exists before accept POST  

## Acceptance criteria

- **Given** a valid client slug, **when** user POSTs a non-empty comment, **then** response is 201 and comment appears in GET for that slug  
- **Given** one or more saved comments, **when** user hard-refreshes the browser, **then** the same comments render in order  
- **Given** unknown slug, **when** user POSTs, **then** 404 with JSON error message (no 500 stack in UI)  

## Out of scope (this task)

- Slack webhook on create (T-02)  
- Styling pass beyond basic list + form  

## Dependencies

- Persistence layer agreed (DB or GitHub API) — blocked until PM/Dev pick per brief spike  

## Files hint

- `src/app/api/portfolio/comments/route.ts`  
- Client detail view component for comment list + form  

## Test notes

- `pnpm run dev` → open client detail for known slug → post → refresh → comment still visible  

## Jira description

**Summary:** Add comment persistence — reload shows saved comments

**Context:**  
Foundation for epic E-01 / story S-01. Need POST+GET by client slug so reload shows saved thread.

**What to build:**  
API routes + client detail load/submit wired to persistence.

**Acceptance:**  
- POST valid slug → 201 + appears in GET  
- Refresh → same comments visible  
- Unknown slug → 404  

**Out of scope:** Slack, styling polish  

**Links:**  
Story: S-01 | Epic: E-01 | Feature: F-03  
Brief: docs/pm/project-brief/OVERVIEW.md  
Local ID: T-01
```

After push: set `jira: PORT-42`. When Done on board, `/aaa-pm-sync` moves file to `tasks/done/`.
