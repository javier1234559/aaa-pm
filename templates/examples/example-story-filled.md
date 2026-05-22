# Example — filled Story (readable first pass)

Maps to one epic **In scope** bullet. Table row + detail block.

## Table row

| ID | Epic | Story | Priority | Jira |
|----|------|-------|----------|------|
| S-01 | E-01 | Users still see their comments after refreshing the page. | Must | |

## Story detail — S-01

**Epic:** E-01 — Support comments on client records and Slack notify

**Summary:**  
Users still see their comments after refreshing the page.

**User story:**  
As an **internal user**, I want **my comments to remain visible after I reload the page**, so that **I can trust the record without re-asking the team**.

**Comes from epic bullet:**  
- Comments persist after every page load

**What "done" means (product level):**  
- A comment posted today is still listed after full browser refresh on the same client  
- Empty state only when no comments exist — not because data failed to load  

**Not in this story:**  
- Slack notification (S-02)  
- Posting UI (S-03) — though T-01 may add minimal UI if required for persistence demo  

**Priority rationale:**  
Must — without persistence, the other stories in the epic have no foundation.

**Jira Story description (paste on push):**  
```
Story: Users still see comments after refreshing the page.
User story: As an internal user, I want comments to remain after reload, so that I trust the client record.
Done when:
- Posted comment visible after full page refresh
- Empty state only when truly no comments
Epic: E-01
Local ID: S-01
Brief: docs/pm/project-brief/OVERVIEW.md
```
