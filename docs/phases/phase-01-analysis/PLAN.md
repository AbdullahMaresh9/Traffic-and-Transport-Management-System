# Implementation Plan — phase-01-analysis

- Phase: **PH-01 — Requirements & Domain Analysis** · Slug: `phase-01-analysis` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-00`
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Elicit, analyze, validate and baseline requirements; establish the domain model; resolve every `OPEN QUESTION`; identify stakeholders and actors; build the traceability chain.

### Out of scope

Anything not derived from the approved requirements baseline (`SYS-03`). Phases 00–02 contain no application implementation (`SYS-01`, `SYS-08`).

## 2. Inputs

| Input | Status |
|---|---|
| Project charter (`../../00-project-charter.md`) | `CONFIRMED` prerequisite |
| Problem context and open questions from Phase 00 | `CONFIRMED` prerequisite |
| `../../../mindmap.md` conceptual hierarchy | `CONFIRMED` prerequisite |
| Stakeholder / supervisor input | `CONFIRMED` prerequisite |
| Rule set + `../../../RULES_HINTS.md` | `CONFIRMED` prerequisite |

## 3. Outputs

| Output | Status |
|---|---|
| Baselined `../../01-requirements.md` | `NOT STARTED` |
| Baselined `../../02-use-cases.md`, `../../03-use-case-actions.md`, `../../04-flow-actions.md`, `../../05-flow-events.md`, `../../06-data-flow.md` | `NOT STARTED` |
| Baselined `../../16-glossary.md` and `../../../mindmap.md` | `NOT STARTED` |
| Completed `../../17-traceability-matrix.md` for every `CONFIRMED` requirement | `NOT STARTED` |
| Resolved `../../15-risk-register.md` entries | `NOT STARTED` |
| Phase audit + session evidence | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Identify stakeholders and validation authority | Interview / brief review | stakeholder register | `BLOCKED (F-006)` |
| A2 | Elicit and catalogue functional requirements (unique, atomic, testable, prioritised) | Document analysis + Q&A | FR list with stable IDs | `NOT STARTED` |
| A3 | Elicit and catalogue non-functional requirements | Quality-attribute workshop | NFR list | `NOT STARTED` |
| A4 | Model use cases (file, descriptions, actions, flows) | Use case modeling | `../../02`–`05` | `NOT STARTED` |
| A5 | Build the domain/concept model and glossary | Domain analysis | `../../16`, `../../../mindmap.md` | `NOT STARTED` |
| A6 | Resolve every Phase 00 `OPEN QUESTION` (or defer with an owner) | Q&A with stakeholder | resolution record | `NOT STARTED` |
| A7 | Complete the traceability matrix for `CONFIRMED` requirements | Traceability rule `SYS-05` | `../../17` | `NOT STARTED` |
| A8 | Validate baseline with stakeholder | Review session | sign-off record | `BLOCKED (F-006)` |
| A9 | Run validator, evaluate exit gate, commit | `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `SYS-03`: no fabricated requirements, stakeholders, integrations or regulations.
- `SYS-04`: every requirement uniquely identified and traceable.
- `SYS-05`: use cases → requirements → risks → design → implementation → tests.
- Application implementation remains forbidden until Phase 01 **and** Phase 02 gates pass (`SYS-08`).

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| No stakeholder → baseline cannot be validated | `CRITICAL` | Escalate before gate evaluation (F-006) |
| Requirements invented by the AI instead of elicited | `HIGH` | `SYS-03` + OPEN QUESTION discipline |
| Scope creep into implementation | `HIGH` | Scope fence `RULES_HINTS.md` SYS-01 |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
