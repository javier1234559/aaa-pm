# Plan: stories first, tasks later

Default for **`/aaa-pm-plan`**. Read before creating epics, stories, or tasks.

## Priority order

1. **Epics** — outcome slices (days to weeks).
2. **Stories** — one clear user benefit each; QA tests at this level.
3. **Tasks** — Dev implementation detail; **not** created during initial plan unless the user asks.

## Story sizing

| Do | Don't |
|----|-------|
| One story = one user-visible benefit | One story = whole epic with many sub-tasks underneath |
| Split epic **In scope** bullets into separate stories | Bundle research + build + sign-off into one story |
| 3–6 acceptance criteria per story | 10+ AC covering unrelated work |
| Product language on stories | APIs, file paths, frameworks on stories |

**Good:** S-01 Research documents Coffee direction · S-02 Interactive mockup deployed · S-03 Design feedback incorporated

**Avoid:** S-01 Validate everything before build → T-01 research, T-02 build, T-03 feedback, T-04 CDP, T-05 sign-off

## Tasks (sub-tasks)

- **Who adds them:** Dev or PO when work starts — **`/aaa-pm-task-add`**, **`/aaa-pm-intake`** (small items), or by asking the agent to break one story down.
- **When plan may create tasks:** Only if the user explicitly requests it (e.g. "also create tasks", "break into sub-tasks").
- **Jira:** Tasks push as **sub-tasks** under a Story only when task files exist and the user asked for sub-tasks. Default push = Epics + Stories only.

## Epic activation

- List **all** epics on OVERVIEW + one file per epic.
- **`inprogress/`** epic(s) get **story files** in `stories/todo/` only (default).
- **`todo/`** / **`done/`** epics — no new story files until activated.

## Task board counts

If no task files exist yet, Task board counts stay `0 | 0 | 0` — that is expected after plan.
