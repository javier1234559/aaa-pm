# Example — filled Story file

**Path:** `docs/pm/jira/stories/S-01-comments-persist.md`

```markdown
---
id: S-01
epic: E-01
priority: Must
jira: PORT-6
---

# Story — [S-01] Users still see their comments after refreshing the page

**Epic:** E-01 — Support comments on client records and Slack notify  
**Priority:** Must  
**Jira:** PORT-6

## Summary
Users still see their comments after refreshing the page.

## User story
As an **internal user**, I want **my comments to remain visible after I reload the page**, so that **I can trust the client record without re-asking the team**.

## From Epic
- Comments persist after every page load

## Acceptance criteria
- A comment posted today is still listed after full browser refresh on the same client
- Empty state only when no comments exist — not because data failed to load

## Not in this story
- Slack notification (S-02)
- Posting UI beyond minimal needed to demonstrate persistence

## Priority rationale
Must — without persistence, the other stories in the epic have no foundation.

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

QA tests **acceptance criteria** here — not individual task files. Dev fills **Handoff QA** before Phase 4.
