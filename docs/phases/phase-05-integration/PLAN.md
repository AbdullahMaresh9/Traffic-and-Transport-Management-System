# Implementation Plan — phase-05-integration

- Phase: **PH-05 — External System Integration** · Slug: `phase-05-integration` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-04` (must be `PASSED`)
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Demonstrate both integration styles: synchronous REST contracts and asynchronous domain events over the broker, through adapters for whichever external systems were confirmed in Phase 01.

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
| Adapter implementations for confirmed boundaries only | `NOT STARTED` |
| Contract tests | `NOT STARTED` |
| Dead-letter handling evidence | `NOT STARTED` |
| Integration security audit | `NOT STARTED` |
| Phase audit + session evidence | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Confirm the list of external systems (from Phase 01 record) | Confirmation review | integration scope list | `OPEN QUESTION` |
| A2 | Implement synchronous REST contracts | Implementation | sync contracts | `NOT STARTED` |
| A3 | Implement asynchronous event publishing/consumption over the broker | Implementation | async flows | `NOT STARTED` |
| A4 | Write contract tests for every confirmed boundary | Testing | contract tests | `NOT STARTED` |
| A5 | Make event consumers idempotent; implement dead-letter handling | Implementation | DLQ evidence | `NOT STARTED` |
| A6 | Test failure paths (timeout, unreachable, malformed, duplicate) | Failure testing | failure evidence | `NOT STARTED` |
| A7 | Integration security audit | Security review | audit record | `NOT STARTED` |
| A8 | Run gates + validator, evaluate exit gate, commit | `GEN-04` + `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `SYS-03`: integrations are never assumed — confirmed in Phase 01 or not built.
- Async flows require correlation, idempotency and dead-letter handling.

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| External systems never confirmed → nothing to integrate | `HIGH` | Resolve in Phase 01 (F-005) before this gate |
| Integration tested only on the happy path | `HIGH` | Failure paths are gate items |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
