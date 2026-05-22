---
name: aaa-pm-push
description: >-
  Create Jira Epics, Stories, and Tasks from docs/pm/jira task files and OVERVIEW via Atlassian MCP.
  Use when user says push, create jira tickets, or jira-push after plan is approved.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — push

## Gate

Read `templates/references/gate.md` and enforce push rules.

Additional:

- At least one task file under `docs/pm/jira/tasks/` OR epics/stories needing keys on OVERVIEW.
- User must **confirm push** in this session.

## Before MCP

1. Read `jira_project_key` from `docs/pm/project-brief/OVERVIEW.md` or `docs/pm/jira/OVERVIEW.md`.
2. Scan:
   - `docs/pm/jira/OVERVIEW.md` — epics/stories with empty `Jira` column
   - `docs/pm/jira/tasks/todo/**/*.md` — files with empty `jira:` in frontmatter (primary push set)
3. List **create plan** in chat: Epic → Story → Task (local IDs + titles).
4. Wait for explicit approval.

## Atlassian MCP

1. Read MCP tool schemas (`plugin-atlassian-atlassian`) before calling.
2. Create order: **Epics → Stories (link Epic) → Tasks (link Story)**.
3. No sub-tasks unless user asked.
4. Descriptions:
   - **Epic:** `## Epic detail — E-XX` → **Jira Epic description** fenced block, or assembled from Why / In scope / Success.
   - **Story:** `## Story detail — S-XX` → **Jira Story description** block.
   - **Task:** full **## Jira description** section from task file (must include Context + Acceptance + `Local ID: T-XX`).
5. Map `type:` frontmatter: BUG→Bug; FEAT/CHANGE→Story/Task; CHORE/SPIKE→Task.
6. Do not transition to Done.

## After create

1. Write keys into task frontmatter `jira:` and OVERVIEW tables.
2. Set `jira_pushed: true` on `docs/pm/jira/OVERVIEW.md` frontmatter.
3. Append row to `docs/pm/plan/CHANGELOG.md` (push event).
4. Summarize: keys created, rows/files skipped.

## Delta push

- Only epics/stories/tasks with empty Jira / empty `jira:`.
- Do not delete or close Jira issues automatically; report orphans if local IDs removed.
