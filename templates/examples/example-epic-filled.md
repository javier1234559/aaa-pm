# Example — filled Epic file

**Path:** `docs/pm/jira/epics/inprogress/E-01-comments-slack.md`  
**OVERVIEW row:** E-01 · IN_PROGRESS · link to this file

```markdown
---
id: E-01
status: IN_PROGRESS
jira: PORT-1
linked_feature: F-03
---

# Epic — [E-01] Support comments on client records and Slack notify

**Status:** IN_PROGRESS  
**Jira:** PORT-1

## Why
Internal users need a single place to leave notes on a client record without switching to Slack or email. Today feedback is scattered; this epic delivers persistence plus team visibility when someone posts.

## Who cares
PM and engineers reviewing a client; leadership wants audit trail on internal discussion (not client-facing chat).

## In scope (outcomes)
- Comments persist after every page load
- New comment sends a team Slack notification
- Internal users can post from the client detail screen

## Out of scope (for this epic)
- Comments on public or client-facing pages
- Search across all comments
- Edit or delete after post

## Success looks like
A user posts on client detail, refreshes the browser, still sees the thread; teammates see a Slack message with client name and excerpt; no webhook secret in the browser.

## Timeline (estimate)
Sprint 1–2

## Risks / dependencies
- Slack webhook URL must be server-side env only
- Persistence choice (DB vs API) must be decided before T-01 ships
```

Full file body is pushed to Jira as the Epic description — no separate paste block.
