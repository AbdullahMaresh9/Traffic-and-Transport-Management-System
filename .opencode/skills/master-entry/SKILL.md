---
name: master-entry
description: Mandatory startup protocol for every TTMS session. Read ENTRY.md, session_track.md, the active phase TODO, RULES_HINTS.md and relevant docs before doing anything; determine truth (DONE/REMAINING/BLOCKED); execute exactly one scope; update tracking files; report Done/Remaining/Next. Load at the start of any session.
---

# Skill — master-entry (session startup & closure)

## Purpose

Guarantee every session resumes from recorded truth instead of assumption, and closes by
updating the tracking files so the next session can continue.

## When to load

Start of **every** session, before any other work. Unload-free: it is short.

## Startup protocol (in order)

1. Read `ENTRY.md` — project identity, active phase, completed/remaining/blocked.
2. Read `session_track.md` — find the latest `OPEN` row; it is the resume point.
3. Read `development_phases_entry.md` — confirm the active phase and its exit gate status.
4. Read the active phase's `TODO.md` under `docs/phases/phase-NN-*/`.
5. Read `RULES_HINTS.md` — binding commands, paths, conventions, status vocabulary.
6. Re-read the architecture/requirements docs relevant to the chosen task **before**
   modifying anything.
7. Determine current truth: `DONE` | `REMAINING` | `BLOCKED` — with evidence, not memory.

## Execution rules

- Select **exactly one** scope per session and execute only that scope.
- Batch clarifying questions (`COM-02`); ask before implementing on ambiguity (`COM-01`).
- Never fabricate requirements, stakeholders, integrations, APIs or regulations (`SYS-03`).

## Closure protocol (in order)

1. Run `python senior-rules/validators/validate.py .` (Windows: `python`, not `python3`)
   and capture the raw output.
2. Update the phase `TODO.md` and `AUDIT.md`.
3. Update `Audit.md` if a finding arose; `memory.md` if a durable fact changed.
4. Update `session_track.md` and write the session file under `docs/sessions/`.
5. Record verification evidence in the session file (`GEN-04`).
6. Commit only after applicable gates pass (`VCS-04`); **ask before pushing**.
7. Report `Done / Remaining / Next` unprompted (`COM-03`, `AUD-04`).

## Output contract

Status vocabulary: `DONE` · `INCOMPLETE` (name the failing gate) · `BLOCKED` (reason +
evidence + unblock condition) · `READY-FOR-REVIEW`. Every claim labelled
`CONFIRMED` / `ASSUMPTION` / `PROPOSED` / `OPEN QUESTION` / `BLOCKED`.
