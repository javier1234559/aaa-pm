# Task file template

**Path:** `docs/pm/jira/tasks/todo/T-NN-<short-kebab-title>.md`  
**Moves:** `todo/` → `inprogress/` → `done/` when status changes (`/aaa-pm-sync` or manual). **Do not rename** the file when moving — only change folder.

**Reader:** A developer or QA opening this file for the first time should understand *why*, *what*, and *how we know it is done* without opening Jira.

Full rules: `templates/references/jira-task-file.md`

---

## File content (copy from here)

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

# <Title — verb + object + outcome>

## Context

**Story:** S-01 — <story summary line from jira/OVERVIEW.md>

**Epic:** E-01 — <epic title>

**Why this task:**  
<2–4 sentences. What gap this closes, who asked for it (CEO intake / bug / tech debt), and what breaks if we skip it.>

**Feature link (brief):** F-XX — <optional, from project-brief §Features>

## What to build

<Plain language description of the deliverable — include UI, API, script, or config change. Be specific enough that another dev knows where to start.>

- <Bullet if multiple parts>
- <…>

## Acceptance criteria

Each line should be **testable** (QA or dev can verify yes/no).

- **Given** <precondition> **when** <action> **then** <expected result>
- Or: <bullet criterion — e.g. "POST with valid body returns 201 and row appears in list">
- <Error case: invalid input returns 400 with message "…">
- <Regression: existing flow X still works>

## Out of scope (this task)

- <Explicitly not doing — avoids ticket creep>
- <Follow-up belongs in T-02 or new story>

## Dependencies

- <Blocked by / needs review from / env vars — or "None">

## Files hint

- `<path or module — optional but recommended>`
- `<…>

## Test notes

- <How to verify locally — command, URL, test account, feature flag>
- <Or "Manual: login → /app → …">

## Jira description

<!-- /aaa-pm-push copies this block into the Jira issue body. Keep Local ID for sync. -->

**Summary:** <Same as H1 title>

**Context:**  
<Short paragraph from ## Context above>

**What to build:**  
<From ## What to build>

**Acceptance:**  
- <mirror Acceptance criteria bullets>

**Out of scope:**  
- <from Out of scope>

**Links:**  
- Story: S-01 | Epic: E-01 | Feature: F-XX  
- Brief: docs/pm/project-brief/OVERVIEW.md  
- Local ID: T-01
```

---

## Frontmatter fields

| Field | Required | Meaning |
|-------|----------|---------|
| `id` | Yes | `T-01` — stable local ID |
| `story` | Yes | Parent `S-XX` |
| `epic` | Yes | Parent `E-XX` |
| `type` | Yes | FEAT, BUG, CHORE, SPIKE, CHANGE |
| `jira` | After push | e.g. `AAAP-43` — empty until `/aaa-pm-push` |
| `priority` | Yes | Must / Should / Could |
| `estimate` | No | e.g. `4h`, `1d` |

---

## Review before push

- [ ] **Context** explains why without reading the whole epic?
- [ ] **Acceptance** has at least 2 testable lines (happy path + one edge/error)?
- [ ] **Out of scope** says what we are not doing in this ticket?
- [ ] **Jira description** block is self-contained for assignee in Jira?
