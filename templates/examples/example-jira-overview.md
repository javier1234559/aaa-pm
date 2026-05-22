# Example — `docs/pm/jira/OVERVIEW.md`

```markdown
---
jira_project_key: PORT
plan_version: "1.0"
jira_pushed: false
active_epics: [E-01]
last_synced_at: null
---

# Jira board

## Epics

| ID | Epic | Status | Jira |
|----|------|--------|------|
| E-01 | Support comments and Slack notify | IN_PROGRESS | |
| E-02 | Replace demo login with production auth | TODO | |

## Active stories

| ID | Epic | Story | Priority | Jira |
|----|------|-------|----------|------|
| S-01 | E-01 | Users still see comments after refreshing the page. | Must | |
| S-02 | E-01 | The team gets notified in Slack when someone posts a comment. | Must | |

## Task board

| Todo | In progress | Done |
|------|-------------|------|
| 3 | 0 | 0 |

## Sync note

_Last sync: —_
```

E-02 has no stories until `IN_PROGRESS`. Tasks live as files under `jira/tasks/todo/`.
