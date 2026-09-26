# AGENTS.md — Operational Entry Point for AI Sessions

> **AI ASSISTANT INSTRUCTION:** Before any work, read `ENTRY.md` at the repository root and
> obey every rule in it. The rules in `senior-rules/` are binding. `RULES_HINTS.md` adapts
> them to this system. Run `python senior-rules/validators/validate.py .` after every
> implementation phase.
>
> *(This instruction block is required by the ADMR installer / ADP-01/ADP-02.)*

---

## What this project is

**Traffic and Transport Management System (TTMS)** — an academic Fourth-Year IT project for
the course *Systems Integration and Architecture*. Read `README.md` for the overview and
`memory.md` for cumulative project state.

## The mandatory startup protocol (do this every session, in order)

1. Read **`ENTRY.md`** — what the project is, what phase is active, what is blocked.
2. Read **`session_track.md`** — the resume index; find the latest `OPEN` row.
3. Read **`development_phases_entry.md`** — identify the **active phase** and its status.
4. Read the **active phase's `TODO.md`** under `docs/phases/phase-NN-*/`.
5. Read **`RULES_HINTS.md`** — this project's binding commands, paths and conventions.
6. Re-read relevant architecture / requirements docs **before modifying anything**.
7. Determine current truth: `DONE` | `REMAINING` | `BLOCKED`.
8. Select **one** execution scope. Execute only that scope.
9. Test, audit, and update documentation in the same commit (DOC-05).
10. Update: phase `TODO.md`, `Audit.md` (if a finding arose), `memory.md` (if a durable
    fact changed), `session_track.md`, and the session file under `docs/sessions/`.
11. Record verification evidence (raw command output) in the session file.
12. Commit only after the applicable gates pass (VCS-04).

## The rules that are always in force

- **`senior-rules/RULES.md`** — 77 rules with stable IDs and severities
  (`CRITICAL` / `HIGH` / `MEDIUM` / `LOW`).
- **Precedence (GEN-07):** `SEC` > `DOD` > `GEN-03` > `IMP` > `DOC`/`AUD` > everything else.
- **Never weaken a CRITICAL rule.** Never edit a rule to make a violation pass
  (`core/00_meta_rules.md` §0.5).
- **Never claim completion without evidence.** If evidence is unavailable, the status is
  `BLOCKED` with the exact reason (GEN-03, DOD-10).
- **Never fabricate requirements, stakeholders, integrations, APIs or regulations**
  (`RULES_HINTS.md` SYS-03). Unresolved input = `OPEN QUESTION`.

## Using the skills — load per phase, never wholesale

Skills live in `.opencode/skills/`. **Do not activate every skill blindly.** Load only what
the current phase/task needs:

| Phase | Load |
|---|---|
| 00 Initialization | `senior-rules`, `master-entry` |
| 01 Requirements | `project-analysis`, `traffic-domain` |
| 02 Architecture | `architecture`, `project-analysis` |
| 03+ Implementation | `parallel-execution`, `senior-rules`, plus domain/architecture skills |
| Any phase, any time | `senior-rules` (the verification layer) |

Specialized agent roles live in `.opencode/agents/` (`architect`,
`requirements-analyst`, `backend`, `frontend`, `integration`, `qa-security`).

## Scope fence in force RIGHT NOW

**PHASE 00 HAS PASSED (`GO`, 41/41). PHASE 01 IS `NOT STARTED` (awaiting explicit user
instruction). NO APPLICATION BUSINESS FUNCTIONALITY MAY BE CREATED.**

Forbidden until Phase 01 *and* Phase 02 exit gates have explicitly passed
(`RULES_HINTS.md` SYS-01 / SYS-08):

- driver / vehicle / license / violation / fine / accident / incident workflows
- traffic dashboards, business APIs, business database models, business services
- production application source code of any kind

If you are tempted to start coding: **stop**, verify `development_phases_entry.md`, and if
Phase 01/02 are not both `PASSED`, report `BLOCKED — SYS-01`.

## Honesty rules for reports

- Use only these statuses: `DONE` · `INCOMPLETE` (name the failing gate) ·
  `BLOCKED` (reason + evidence + what would unblock) · `READY-FOR-REVIEW`.
- Label every material claim: `CONFIRMED` · `ASSUMPTION` · `PROPOSED` ·
  `OPEN QUESTION` · `BLOCKED`.
- Ambiguity → **ask before implementing** (COM-01), and batch the questions (COM-02).
- A phase report must state **Done / Remaining / Next** unprompted (COM-03, AUD-04).

## Where things live

| I need… | Go to |
|---|---|
| Orientation / current status | `ENTRY.md` |
| Resume point | `session_track.md` |
| Phase registry & exit gates | `development_phases_entry.md` |
| Full project timeline | `all_in_one_track.md` |
| Architecture | `architecture.md` |
| Domain concepts | `mindmap.md` |
| Cumulative state & conventions | `memory.md` |
| Findings & audit register | `Audit.md` |
| Mandatory rules | `senior-rules/RULES.md` |
| This project's binding adapter | `RULES_HINTS.md` |
| Detailed analysis & design docs | `docs/` |
| Phase artifacts | `docs/phases/phase-NN-*/` |
| Session evidence | `docs/sessions/` |
| Decision records | `docs/decisions/` |
| Traceability | `docs/17-traceability-matrix.md` |
