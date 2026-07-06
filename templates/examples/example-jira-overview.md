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

| ID | Epic | Status | File | Jira |
|----|------|--------|------|------|
| E-01 | Support comments and Slack notify | IN_PROGRESS | [E-01-comments-slack.md](../epics/E-01-comments-slack.md) | |
| E-02 | Replace demo login with production auth | TODO | [E-02-prod-auth.md](../epics/E-02-prod-auth.md) | |

## Active stories

| ID | Epic | Story | Priority | File | Jira |
|----|------|-------|----------|------|------|
| S-01 | E-01 | Users still see comments after refreshing the page. | Must | [S-01-comments-persist.md](../stories/S-01-comments-persist.md) | |
| S-02 | E-01 | The team gets notified in Slack when someone posts a comment. | Must | [S-02-slack-notify.md](../stories/S-02-slack-notify.md) | |

## Task board

| Todo | In progress | Done |
|------|-------------|------|
| 3 | 0 | 0 |

## Sync note

_Last sync: —_
```

Detail in `jira/epics/{todo,inprogress,done}/` and `jira/stories/{todo,inprogress,done}/`. Tasks in `jira/tasks/todo/`. E-02 has no active stories until moved to `inprogress/`.
