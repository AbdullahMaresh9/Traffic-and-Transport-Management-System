---
name: project-analysis
description: Structured analysis skill for TTMS documentation and requirements work. Use when cataloguing requirements, reviewing documents for the required section structure, classifying findings, or assessing whether a document may claim a status. Enforces Purpose/Scope/Status sections and CONFIRMED/ASSUMPTION/PROPOSED/OPEN QUESTION/BLOCKED labels.
---

# Skill — project-analysis (document & requirements analysis)

## Purpose

Make analysis output consistent and auditable: same sections, same labels, same severity
model — so findings can be compared across phases.

## When to load

- Phase 01 requirements work; any document review; any findings classification.

## Required document structure

Every project document must carry: **Purpose · Scope · Current Status · Known Context ·
Confirmed Information · Assumptions · Open Questions · Tables · Traceability · Related
Documents.** A document missing these is a `DOC-*` finding, not a pass.

## Claim labelling (mandatory)

| Label | Meaning |
|---|---|
| `CONFIRMED` | Sourced from a real input in this repo or the brief |
| `ASSUMPTION` | Author's assumption, unconfirmed |
| `PROPOSED` | Suggested option, not yet decided |
| `OPEN QUESTION` | Needs a human answer; never silently resolved |
| `BLOCKED` | Cannot proceed; states the exact unblock condition |

## Analysis procedure

1. Inventory the subject (files, rules, skills, artifacts) before judging it.
2. Classify: Planning / Architecture / Requirements / Implementation / Testing / Security /
   Documentation / Orchestration / Operations.
3. Detect conflicts against project constraints, existing state and the rule set; record
   each conflict as a finding with rule ID + severity.
4. Adapt explicitly: state what was adopted, rejected or deferred **and why**
   (`memory.md` lessons, `Audit.md` findings).
5. Never fabricate inputs; unresolved input = `OPEN QUESTION` (`SYS-03`).

## Severity model

Match `senior-rules/RULES.md`: `CRITICAL` · `HIGH` · `MEDIUM` · `LOW`. A phase cannot close
with open `CRITICAL`/`HIGH` (`AUD-02`).

## Output contract

Tables over prose; every row labelled; end with Done / Remaining / Next (`COM-03`).
