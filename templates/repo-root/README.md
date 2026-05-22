## docs/pm — AAA PM

Solo PM workspace: product brief, intake archive, plan log, and Jira-backed task files.

### Start here

Tag `@docs/pm/AGENTS.md` or run `/aaa-pm-about`.

### Layout

```
docs/pm/
├── AGENTS.md
├── project-brief/OVERVIEW.md   ← product truth
├── intake/OVERVIEW.md          ← feedback index
├── intake/raw-intake/          ← one file per paste
├── plan/CHANGELOG.md           ← plan / push events
└── jira/
    ├── OVERVIEW.md             ← epics + active stories
    └── tasks/{todo,inprogress,done}/
```

### Typical flow

1. `/aaa-pm-setup` — scaffold (first time)
2. `/aaa-pm-plan` — epics, stories, task files in `tasks/todo/`
3. `/aaa-pm-push` — create Jira from task files
4. `/aaa-pm-task-doing` — start one ticket
5. `/aaa-pm-sync` — Jira status → move task files
6. `/aaa-pm-intake` — paste CEO/client feedback
