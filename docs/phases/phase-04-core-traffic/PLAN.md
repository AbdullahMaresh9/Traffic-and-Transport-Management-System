# Implementation Plan — phase-04-core-traffic

- Phase: **PH-04 — Core Traffic Domain** · Slug: `phase-04-core-traffic` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-03` (must be `PASSED`)
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Implement the core traffic domain and its supporting domains end-to-end: drivers, vehicles, licenses, violations, fines, penalty points, accidents, incidents, monitoring, signals, reporting and notifications.

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
| Implemented core domain (backend + data layer) | `NOT STARTED` |
| Full CORE-03 artifact set (use cases, DFD, state machines, sequence/activity diagrams, test plan, permissions matrix, QA file, security audit) | `NOT STARTED` |
| State machines for every lifecycle-bearing entity | `NOT STARTED` |
| Tests: happy path + validation + authorization per function | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Implement data schema and migrations for the domain | Implementation | schema | `NOT STARTED` |
| A2 | Implement driver / vehicle / license services + endpoints | Implementation | domain modules | `NOT STARTED` |
| A3 | Implement violation / fine / penalty-point services + endpoints | Implementation | domain modules | `NOT STARTED` |
| A4 | Implement accident / incident / monitoring / signal services | Implementation | domain modules | `NOT STARTED` |
| A5 | Implement reporting / notification services | Implementation | domain modules | `NOT STARTED` |
| A6 | Author CORE-03 artifacts (use cases, DFD, state machines, diagrams, test plan, permissions matrix) | Documentation | CORE-03 set | `NOT STARTED` |
| A7 | Permissions enforced server-side with tests; 0 dead elements | Verification | test evidence | `NOT STARTED` |
| A8 | Run all gates G1–G9 + validator, evaluate exit gate, commit | `GEN-04` + `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `IMP-01`…`IMP-03`: wiring, no dead elements, server-side permissions.
- `SEC-01`: no secrets; `DOC-05`: docs in the same commit.
- Feature/domain work lives **inside** this phase; feature-based 'phases' are not used (`AP-06`).

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| Implementation starts from unapproved design | `CRITICAL` | Hard dependency on Phase 02/03 gates |
| Lifecycle behavior implemented without state machines | `HIGH` | State machines are gate items |
| Coverage target missed at the end | `HIGH` | Tests written with each feature |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
