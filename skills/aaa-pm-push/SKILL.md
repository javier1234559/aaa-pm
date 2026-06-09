---
name: aaa-pm-push
description: >-
  Create Jira Epics, Stories, and Tasks from docs/pm/jira epic/story/task files via Atlassian MCP.
  Full markdown body = Jira description. Use after plan is approved.
disable-model-invocation: true
metadata:
  pack: aaa-pm
---

# AAA PM — push

## Gate

Read `templates/references/gate.md` and enforce push rules.

Additional:

- At least one of: epic file, story file, task file needing keys — or OVERVIEW rows with empty `Jira`.
- User must **confirm push** in this session.

## Before MCP

1. Read `jira_project_key` from `docs/pm/project-brief/OVERVIEW.md` or `docs/pm/jira/OVERVIEW.md`.
2. Scan:
   - `docs/pm/jira/epics/*.md` — empty `jira:` in frontmatter or empty OVERVIEW Jira column
   - `docs/pm/jira/stories/*.md` — same (active epics only)
   - `docs/pm/jira/tasks/todo/**/*.md` — empty `jira:` in frontmatter
3. List **create plan** in chat: Epic → Story → Task (local IDs + titles).
4. Wait for explicit approval.

## Atlassian MCP

1. Read MCP tool schemas (`plugin-atlassian-atlassian`) before calling.
2. Create order: **Epics → Stories (link Epic) → Tasks (link Story)**.
3. No sub-tasks unless user asked.
4. **Descriptions** — use full markdown file body (from `# Title` or first heading through end):
   - **Epic:** `docs/pm/jira/epics/E-NN-*.md`
   - **Story:** `docs/pm/jira/stories/S-NN-*.md`
   - **Task:** task file (exclude YAML frontmatter; include body sections)
   - Ensure `Local ID: E-XX` / `S-XX` / `T-XX` appears in description for sync.
5. Map `type:` frontmatter: BUG→Bug; FEAT/CHANGE→Story/Task; CHORE/SPIKE→Task.
6. Do not transition to Done.

## After create

1. Write keys into epic/story frontmatter `jira:` and OVERVIEW table columns; task frontmatter `jira:`.
2. Set `jira_pushed: true` on `docs/pm/jira/OVERVIEW.md` frontmatter.
3. Append row to `docs/pm/plan/CHANGELOG.md` (push event).
4. Summarize: keys created, rows/files skipped.

## Delta push

- Only items with empty Jira / empty `jira:`.
- Do not delete or close Jira issues automatically; report orphans if local IDs removed.
