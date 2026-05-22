---
id: T-15
story: S-13
epic: E-07
type: FEAT
jira: AAAP-43
priority: Must
estimate: 1d
---

# Revenue chart — monthly view only

## Context

**Story:** S-13 — Revenue chart uses monthly view only.

**Epic:** E-07 — Enhance portfolio dashboard

**Why this task:**  
CEO intake (2026-05-18): week/bi-week toggles confuse leadership; monthly is the only view they want on `/app`. This task implements that decision on the existing chart component.

**Feature link (brief):** F-04 — Commercial / revenue rollup

## What to build

- Remove Week and Bi-week controls from dashboard revenue chart  
- Aggregate `commercial.entries` (or inferred totals) by **calendar month**  
- Default view = monthly on load  

## Acceptance criteria

- **Given** dashboard `/app`, **when** page loads, **then** revenue chart shows monthly buckets only (no period toggle)  
- **Given** project YAML with `commercial.entries`, **when** chart renders, **then** amounts match month boundaries in config  
- **Given** light/dark theme, **when** toggling theme, **then** chart still renders monthly data correctly  

## Out of scope (this task)

- Pipeline metric card (T-16)  
- Four phase summary cards (T-17)  

## Dependencies

- None — chart component already exists; this is UX + aggregation change  

## Files hint

- Dashboard revenue chart component under `src/` (see repo conventions)  

## Test notes

- `pnpm run dev` → `/app` → verify single monthly chart, no week/bi-week UI  

## Jira description

**Summary:** Revenue chart — monthly view only

**Context:**  
CEO spec: drop week/bi-week toggles; monthly aggregation only on portfolio dashboard (E-07 / S-13).

**What to build:**  
Remove toggles; aggregate by calendar month from `commercial.entries`.

**Acceptance:**  
- Monthly-only on load  
- Data matches YAML month boundaries  
- Works in light/dark  

**Out of scope:** Pipeline metric, phase cards  

**Links:**  
Story: S-13 | Epic: E-07 | Feature: F-04  
Brief: docs/pm/project-brief/OVERVIEW.md  
Local ID: T-15
