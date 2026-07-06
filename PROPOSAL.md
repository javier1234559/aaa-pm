# PM Ticket Templates

*Appendix to **Streamlined Operations in the Age of AI**. Defines Epic, Story, and Task content and how the team uses them on Jira.*

---

## Overview

This document is the **detail layer** for project management tickets. The main proposal covers roles (CEO, PO, Dev), phases, and pilot intent. Here we only cover **what each ticket type contains** and **how the team fills and uses them**.

Work breaks down in three levels:

**Epic** — A large slice of the project (days to weeks). Describes outcomes and boundaries, not individual dev tasks.

**Story** — One clear benefit for the end user. Written in product language. QA tests at this level.

**Task** — Concrete work for Dev to implement a story. Technical detail lives here only.

One rule applies everywhere: **the same markdown goes in the repo and in the Jira description**. There is no separate shortened version for Jira.

Supporting pieces outside the three ticket types:

`**docs/qa/ACCESS.md*`* — Created once per project. Staging URL, login, seed data, Figma/spec links. Shared for all testing.

**Handoff QA** — A section on each Story. Left empty when planning. Dev fills it before QA tests so QA knows the path and data without guessing the UI.

**Definition of Done** — A short checklist on every Story. QA runs it at the end of Phase 4 to confirm the story is truly complete — not just "acceptance criteria passed once." The same checklist applies to every story unless a story explicitly notes an exception.

---

## Templates

Templates use `<!-- comments -->` as inline guidance. Remove comments when copying into Jira if your project renders them; they are safe to keep in repo copies.

### Test access (project file)

Path: `docs/qa/ACCESS.md`

```markdown
# Test access — [Project name]
<!-- One file per project. PO or Dev creates at Phase 2. QA uses this for every story — do not repeat URL/login on each Story. -->

**Staging / preview:** 
**Login:** 
**Seed / default data:** 
**Figma / spec:** 
**Other links:** 
```

---

### Epic

```markdown
# Epic — [E-XX] [Short verb-led title]
<!-- PO writes at Phase 2. Outcomes only — no dev tasks, file paths, or APIs. CEO reads at this level. -->

**Status:** TODO | IN_PROGRESS | DONE  
**Jira:** 
<!-- Fill after push to Jira. Same content lives in repo and Jira description. -->

## Why
[2–3 sentences: client problem, why this chunk is one epic]

## Who cares
[Stakeholders who benefit]

## In scope (outcomes)
<!-- User-visible results. Each bullet often becomes one Story. -->
- 
- 
- 

## Out of scope
<!-- Prevents scope creep. List at least one real exclusion. -->
- 
- 

## Success looks like
<!-- Outcome when the epic is done — not "all tickets closed." QA signs off all stories in this epic. -->

## Timeline (estimate)
[e.g. Sprint 1–2 / Week 3–4 / TBD]

## Risks / dependencies
- [or "None"]
```

---

### Story

```markdown
# Story — [S-XX] [One sentence — user benefit]
<!-- PO writes at Phase 2. Product language only — no APIs, frameworks, or file paths (those go in Tasks). -->

**Epic:** E-XX — [epic title]  
**Priority:** Must | Should | Could  
**Jira:** 

## Summary
[Same as title — who gets what]

## User story
As a [role], I want [capability], so that [benefit].

## From Epic
- [Matching "In scope" bullet from parent epic]

## Acceptance criteria
<!-- WHAT the feature must do — unique per story. QA tests each bullet in Phase 4. -->
<!-- Product / user perspective. 3–6 bullets: happy path + edge case. Not the same as Definition of Done below. -->
- 
- 
- 

## Not in this story
<!-- Stops overlap with neighboring stories. -->
- 

## Priority rationale
[One sentence]

## Handoff QA
<!-- WHERE and HOW to test — Dev fills before QA starts Phase 4. Leave bullets empty at plan time. -->
<!-- QA does not test without this section filled. Login URL lives in ACCESS.md, not here. -->

Project test access: `docs/qa/ACCESS.md`

- **Path:** 
<!-- Clicks from login to the screen under test, e.g. Login → Cases → List -->
- **Data for this story:** 
<!-- Seed or account needed for this story only, e.g. 2 study-abroad + 1 residency -->
- **Notes:** 
<!-- Feature flags, branch, breakpoint — or "None" -->

## Definition of Done
<!-- WHEN the story is ship-ready — same checklist every story. QA ticks at end of Phase 4. -->
<!-- Does NOT replace acceptance criteria: AC = what works; DoD = quality gates + confirm AC was fully verified. -->

- [ ] All acceptance criteria pass on staging
- [ ] Handoff QA filled — path and data verified
- [ ] No open Blocker or Critical bugs linked to this story
- [ ] Feature visible on staging matches what Dev demoed
- [ ] Regression: related flows still work (or "N/A" with reason)
```

---

### Task

```markdown
# Task — [T-XX] [Verb + concrete deliverable]
<!-- Dev writes (PO may draft). Technical detail lives here only. QA does not test Tasks individually — QA tests the parent Story. -->

**Story:** S-XX — [story summary]  
**Epic:** E-XX — [epic title]  
**Type:** FEAT | BUG | CHORE  
**Priority:** Must | Should | Could  
**Estimate:** [4h | 1d | …]  
**Jira:** 

## Context
[Why this task exists — 2–4 sentences]

## What to build
<!-- APIs, UI, config — be specific enough for another dev to start. -->

## Done when
<!-- Dev self-checks before handing story to QA. Not the same as Story Definition of Done. -->
<!-- Technical yes/no checks. Roll path + data into Story Handoff QA when the whole story is ready. -->
- 
- 

## Out of scope
- 

## Dependencies
[None or list]
```

*Dev rolls path and data into the parent Story's **Handoff QA** when the story is ready — not duplicated on every Task.*

---

## How to use

Below is one end-to-end pass: immigration case management. Each step shows **who acts**, **what they write**, and **which template section matters**.

---

### Step 1 — Kick off access (once per project)

After Phase 2 clarification, PO or Dev creates `docs/qa/ACCESS.md` so nobody asks for the staging URL twice.

```markdown
# Test access — Immigration case app

**Staging / preview:** https://staging.example.com
**Login:** demo@client.com (1Password vault: Immigration Dev)
**Seed / default data:** `pnpm db:seed` — 2 study-abroad cases, 1 residency
**Figma / spec:** https://figma.com/…
**Other links:** Slack channel #immigration-dev
```

This file stays fixed unless the environment changes.

---

### Step 2 — PO writes the Epic (Phase 2)

PO turns the agreed scope into Epic **E-01** and pushes the full block to Jira.

```markdown
# Epic — [E-01] Basic case management

**Status:** IN_PROGRESS  
**Jira:** IMM-1

## Why
The firm still runs cases in Excel. Phase one needs one place to view, create, and open cases before approval workflows.

## Who cares
Consulting staff (daily use); client (professional delivery); CEO (staging demo).

## In scope (outcomes)
- Staff view a case list and filter by application type
- Staff create a new case with required fields
- Staff open a case and see current status

## Out of scope
- Multi-level approval (Epic E-02)
- PDF export / automated email
- Full-text search

## Success looks like
Staff run a typical day on the app without Excel. QA signs off three stories; CEO demos on staging.

## Timeline (estimate)
Sprint 1–2 (~2 weeks)

## Risks / dependencies
- Client confirms application types before Sprint 1
```

CEO reads the board at Epic level. Stories and tasks are added only for epics marked **IN_PROGRESS**.

---

### Step 3 — PO writes the Story (Phase 2)

Each bullet under **In scope** becomes a story. **Acceptance criteria** are how QA will test later. **Handoff QA** and **Definition of Done** checkboxes stay empty or unchecked at plan time.

```markdown
# Story — [S-01] Staff view the case list and filter by application type

**Epic:** E-01 — Basic case management  
**Priority:** Must  
**Jira:** IMM-6

## Summary
After login, staff see a case list and can filter by application type.

## User story
As a **consulting staff member**, I want **to view and filter the case list**, so that **I can find the right case without Excel**.

## From Epic
- Staff view a case list and filter by application type

## Acceptance criteria
- After login, the list shows client name, application type, and status
- Filter "Study abroad" shows only study-abroad cases; "All" restores the full list
- No cases shows a clear empty state — not a blank screen or error
- Default sort is newest first

## Not in this story
- Create case (S-02)
- Case detail (S-03)

## Priority rationale
No list means no client demo.

## Handoff QA

Project test access: `docs/qa/ACCESS.md`

- **Path:** 
- **Data for this story:** 
- **Notes:** 

## Definition of Done

- [ ] All acceptance criteria pass on staging
- [ ] Handoff QA filled — path and data verified
- [ ] No open Blocker or Critical bugs linked to this story
- [ ] Feature visible on staging matches what Dev demoed
- [ ] Regression: related flows still work (or "N/A" with reason)
```

At plan time, empty Handoff bullets and unchecked DoD boxes are intentional. QA only needs clear **what** "done" means in acceptance criteria — not URLs or clicks yet.

---

### Step 4 — Dev adds Tasks and implements (Phase 3)

Dev breaks S-01 into tasks. Example: API work.

```markdown
# Task — [T-02] Case list API with application-type filter

**Story:** S-01 — Staff view the case list and filter by application type  
**Epic:** E-01 — Basic case management  
**Type:** FEAT  
**Priority:** Must  
**Estimate:** 1d  
**Jira:** IMM-10

## Context
S-01 needs server data. List UI (T-01) depends on this endpoint.

## What to build
- GET `/api/cases` with optional `type` filter and pagination
- Authenticated access only

## Done when
- Unfiltered GET → 200, newest first
- `?type=study_abroad` → only matching cases
- Invalid type → 400; unauthenticated → 401
- Automated test for happy path + filter

## Out of scope
- List UI (T-01)
- Create / update / delete

## Dependencies
- `cases` schema and enums confirmed by client
```

Dev moves tasks on the board: To Do → In Progress → Done. Dev self-checks against **Done when** before handing the story to QA.

Other tasks for the same story (e.g. T-01 list UI, T-03 wire frontend) follow the same Task template.

---

### Step 5 — Dev fills Handoff QA and notifies QA (end of Phase 3)

When all tasks for S-01 are done and deployed to staging, Dev completes **Handoff QA** on the Story (same content in Jira).

```markdown
## Handoff QA

Project test access: `docs/qa/ACCESS.md`

- **Path:** Login → left nav "Cases" → "List"
- **Data for this story:** Default seed (2 study abroad, 1 residency); empty state: `empty@…`
- **Notes:** None
```

Dev posts on the project channel: *S-01 ready for QA.*

If Handoff is still empty, QA sends it back — no Phase 4 test until path and data are filled.

---

### Step 6 — QA tests the Story (Phase 4)

QA opens three things in order:

1. `docs/qa/ACCESS.md` — log in on staging
2. Story **Handoff QA** — navigate to the list, use the right data
3. Story **Acceptance criteria** — verify each bullet pass or fail

QA does not read every Task. When all acceptance criteria pass, run **Definition of Done** — tick each checkbox on the Story. All boxes checked means S-01 is complete.

If filter still shows residency cases under "Study abroad," QA opens a **Bug** linked to S-01 (repro steps, actual vs expected). Dev fixes in a dedicated block; QA re-tests the same acceptance criteria and DoD checklist.

---

### Step 7 — Close the Epic (Phase 5)

When S-01, S-02, and S-03 all pass QA (acceptance criteria + Definition of Done), Epic E-01 meets **Success looks like**. QA records a walkthrough video for the CEO. Client UAT follows the main proposal.

The next epic (E-02) gets its own Epic template when it moves to **IN_PROGRESS**.

---

### Quick reference

**PO at plan time:** Epic + Story (acceptance criteria). Handoff QA empty. Definition of Done unchecked. Create ACCESS once.

**Dev while building:** Tasks with **Done when**. Update board status.

**Dev before QA:** Fill Handoff QA on the Story.

**QA at test time:** ACCESS → Handoff → acceptance criteria → Definition of Done checklist. No test without Handoff.

**CEO:** Epic titles and phase outcomes from the main proposal — not required to open Tasks.

---

*For roles, five phases, and pilot decision, see **Streamlined Operations in the Age of AI**.*

---

## Bonus — PO workflow using AI skills

*Internal reference for the PO only. Implements this document via the **`aaa-pm`** skill pack (`docs/pm/` + Jira). CEO does not need this section.*

### Skills you use

The **`aaa-pm`** pack exposes these commands in Cursor:

- **`/aaa-pm-about`** — Pack layout and which skill to run next.
- **`/aaa-pm-setup`** — Scaffold `docs/pm/` and complete the project brief (new project or brief not finished).
- **`/aaa-pm-plan`** — Phase 2: Epics + Stories from the brief (one story per user benefit; **no task files** unless you ask). Handoff QA and DoD left empty at plan time.
- **`/aaa-pm-push`** — Create or update Jira issues after you approve the plan in chat.
- **`/aaa-pm-intake`** — Paste CEO/client feedback into `intake/raw-intake/` and update brief or backlog.
- **`/aaa-pm-sync`** — Pull new Jira tasks into `tasks/todo/`, backfill `jira:` keys, reconcile **todo folders only** (default). Say **`sync full`** to reconcile all folders.
- **`/aaa-pm-task-start`** — Dev picks a task by ID/name → moves to inprogress → presents implementation plan for approval.
- **`/aaa-pm-task-done`** — Dev marks task done after review; moves file to `tasks/done/`.
- **`/aaa-pm-task-add`** — Add emergent tasks to a story without full re-plan.

**Dev** uses `task-start` → implement → `task-done` daily. **PO** uses setup → plan → push → intake → sync. Phase 4 QA in this proposal is manual (ACCESS → Handoff → acceptance criteria → DoD) until the pack adds a dedicated QA skill.

Atlassian MCP is used inside `push` and `sync` — you do not need separate Jira skills.

### Skills mapped to phases

**Phase 1 — Intake**  
CEO collects requirements. You run **`/aaa-pm-intake`** with proposal or transcript, or add files under `docs/pm/intake/raw-intake/`. Skip `plan` until `brief_status: complete` on the project brief.

**Phase 2 — Clarify and standardize**  
After the three-way meeting: **`/aaa-pm-plan`** → review epic/story tree in chat → approve → **`/aaa-pm-push`**. Dev adds task files when implementation starts. Create **`docs/qa/ACCESS.md`** on first plan (or during setup once the pack scaffolds it).

**Phase 3 — Execution**  
Dev codes; primary direction is **local → Jira** via `push`. Run **`/aaa-pm-sync`** when a second dev adds tickets on Jira (default pulls new tasks into `tasks/todo/` only). Dev uses **`/aaa-pm-task-start`** → approve plan → implement → **`/aaa-pm-task-done`**. Emergent tasks → **`/aaa-pm-task-add`**. Dev fills **Handoff QA** on the Story and posts *ready for QA* on the project channel.

**Phase 4 — Testing**  
You act as QA: follow Step 6 in **How to use** above. No aaa-pm skill yet — open the Story file and `ACCESS.md`.

**Phase 5 — Delivery**  
Walkthrough video and CEO demo — outside the pack.

**Scope change** — large: `intake` → `plan` → `push`. Small: `intake` → new task file → `push` (delta). **Board drift:** `sync`.

### Fast paths by situation

**New project**

```
/aaa-pm-setup  →  complete brief  →  docs/qa/ACCESS.md
→  /aaa-pm-plan  →  you approve  →  /aaa-pm-push
```

**Typical PO week**

- Start of week: `/aaa-pm-sync` if dev 2 may have added Jira tasks. Re-plan only if scope shifted (`plan` + `push`).
- Mid-week: `/aaa-pm-intake` only when CEO or client sends feedback.
- When Dev says a story is ready: check Handoff QA is filled, then run Phase 4 QA.
- End of week: `/aaa-pm-sync` to pull any new Jira tasks into `tasks/todo/`.

**New tickets without re-planning the whole epic**  
Add task files with **`/aaa-pm-task-add`**, then **`/aaa-pm-push`** (delta — only items missing Jira keys).

### Habits that save time

1. **One chat, one job** — Separate sessions for `plan`, `push`, and `sync`. Confirm before `push`.
2. **Brief complete before `plan`** — The pack gate avoids vague epics.
3. **No Phase 4 without Handoff** — Dev fills path and data; you do not guess the UI.
4. **Sync when Jira gains tickets** — Default sync is incremental (todo + inbound only). Use **`sync full`** only after long board drift.
5. **Repo content = Jira description** — Edit Story/Task files under `docs/pm/`, then push or sync; do not edit Jira in isolation.
6. **`/aaa-pm-about` when unsure** — Stops the agent from mixing PM work with implementation.

### Skill flow (PO view)

```
CEO intake (channel)
       ↓
PO: /aaa-pm-intake
       ↓
PO: /aaa-pm-setup  (once)
       ↓
PO: /aaa-pm-plan  →  approve  →  /aaa-pm-push
       ↓
Dev: /aaa-pm-task-start  →  approve  →  implement  →  /aaa-pm-task-done
       ↓ (emergent work)
     /aaa-pm-task-add  →  /aaa-pm-push (delta)
       ↓
PO: /aaa-pm-sync  (scheduled)
       ↓
Dev: Handoff QA on Story  →  "ready for QA"
       ↓
PO as QA: PROPOSAL How to use Step 6
       ↓
CEO demo / UAT  (main proposal)
```

---
