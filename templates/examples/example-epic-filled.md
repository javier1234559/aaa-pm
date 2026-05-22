# Example — filled Epic (readable first pass)

Feature **F-03** from brief. Table row + detail block for `jira/OVERVIEW.md`.

## Table row

| ID | Epic | Status | Jira |
|----|------|--------|------|
| E-01 | Support comments on client records and Slack notify | IN_PROGRESS | |

## Epic detail — E-01

**Title:** Support comments on client records and Slack notify

**Linked feature (brief):** F-03 — Internal comments on client detail with optional Slack alert

**Why this epic exists:**  
Internal users need a single place to leave notes on a client record without switching to Slack or email. Today feedback is scattered; this epic delivers persistence plus team visibility when someone posts.

**Who cares:**  
PM and engineers reviewing a client; leadership wants audit trail on internal discussion (not client-facing chat).

**In scope (outcomes):**  
- Comments persist after every page load  
- New comment sends a team Slack notification  
- Internal users can post from the client detail screen  

**Out of scope (for this epic):**  
- Comments on public or client-facing pages  
- Search across all comments  
- Edit or delete after post  

**Success looks like:**  
A user posts on client detail, refreshes the browser, still sees the thread; teammates see a Slack message with client name and excerpt; no webhook secret in the browser.

**Dependencies / risks:**  
- Slack webhook URL must be server-side env only  
- Persistence choice (DB vs API) must be decided before T-01 ships  

**Jira Epic description (paste on push):**  
```
Goal: Internal comments on client records with Slack notify
In scope:
- Comments persist after reload
- Slack on new comment
- Post form on client detail
Out of scope:
- Public pages, search, edit/delete
Success: Post → refresh → visible; Slack received; secrets server-only
Feature: F-03
Local ID: E-01
Brief: docs/pm/project-brief/OVERVIEW.md
```
