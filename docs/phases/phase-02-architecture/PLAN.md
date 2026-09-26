# Implementation Plan — phase-02-architecture

- Phase: **PH-02 — Architecture & Integration Design** · Slug: `phase-02-architecture` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-01` (must be `PASSED`)
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Convert every `PROPOSED` architectural hypothesis into accepted ADRs; produce C4 views, data model, API contract, integration design, security design and technology justification.

### Out of scope

Anything not derived from the approved requirements baseline (`SYS-03`). Phases 00–02 contain no application implementation (`SYS-01`, `SYS-08`).

## 2. Inputs

| Input | Status |
|---|---|
| Previous phase outputs | `CONFIRMED` prerequisite |
| Rule set + `../../../RULES_HINTS.md` | `CONFIRMED` prerequisite |
| `../../../architecture.md` | `CONFIRMED` prerequisite |

## 3. Outputs

| Output | Status |
|---|---|
| Updated `../../../architecture.md` (delta section) | `NOT STARTED` |
| Accepted ADRs in `../../decisions/` | `NOT STARTED` |
| `../../09-database.md`, `../../10-api-specification.md`, `../../11-integration-specification.md`, `../../12-security-specification.md`, `../../14-quality-attributes.md` | `NOT STARTED` |
| Architecture threat model | `NOT STARTED` |
| Phase audit + session evidence | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Rank quality attributes and driving forces | Attribute ranking | `../../14` finalized | `NOT STARTED` |
| A2 | Produce C4 context/container/component views | Architectural modeling | C4 views | `NOT STARTED` |
| A3 | Design data model outline and API contract | Contract-first design | `../../09`, `../../10` | `NOT STARTED` |
| A4 | Design integration (sync REST + async events) | Integration analysis | `../../11` | `NOT STARTED` |
| A5 | Design security architecture + threat model | Threat modeling | `../../12` + threat model | `NOT STARTED` |
| A6 | Complete technology evaluation matrix vs `../../../RULES_HINTS.md` §2 | Evaluation matrix | matrix + conformity check | `NOT STARTED` |
| A7 | Record every decision as an ADR; reject or accept each `PROPOSED` item | ADR process | `../../decisions/` | `NOT STARTED` |
| A8 | Architecture review: all requirements traceable to design elements | Traceability check | `../../17` links | `NOT STARTED` |
| A9 | Run validator, evaluate exit gate, commit | `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `SYS-06`: architecture decisions documented as ADRs before implementation.
- `SEC-*`: security architecture designed before code.
- Stack stays `PROPOSED` until its ADR is accepted; deviations from `RULES_HINTS.md` §2 require the user's decision.
- Implementation remains forbidden until Phase 01 **and** Phase 02 gates pass (`SYS-08`).

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| Architecture decided before requirements are validated | `HIGH` | Hard dependency on Phase 01 gate |
| Stack chosen by habit instead of evaluation | `HIGH` | Technology evaluation matrix required by gate |
| External integrations assumed without confirmation | `HIGH` | `SYS-03` — `PROPOSED` until confirmed |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
