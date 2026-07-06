## docs/pm — AAA PM

Solo PM workspace: product brief, intake archive, plan log, and Jira-backed epic/story/task files.

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
    ├── OVERVIEW.md             ← epics + stories + board counts
    ├── epics/{todo,inprogress,done}/
    ├── stories/{todo,inprogress,done}/
    └── tasks/{todo,inprogress,done}/
```

### Typical flow

1. `/aaa-pm-setup` — scaffold (first time)
2. `/aaa-pm-plan` — epics + stories (tasks when you start work or ask)
3. `/aaa-pm-push` — create Jira from epic/story files (tasks if any)
4. `/aaa-pm-task-start` — pick task → plan for approval → implement
5. `/aaa-pm-task-done` — mark task done after review
6. `/aaa-pm-task-add` — add emergent tasks mid-implementation
7. `/aaa-pm-sync` — Jira status → move epic/story/task files
8. `/aaa-pm-intake` — paste CEO/client feedback
