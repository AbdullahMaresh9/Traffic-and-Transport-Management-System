# 13 — Testing Strategy

| Field | Value |
|---|---|
| **Purpose** | Define the test levels, coverage targets, required suites and the gate that evidence must satisfy. |
| **Scope** | Strategy and targets only. **No tests exist or can run yet.** |
| **Current Status** | `PROPOSED` strategy (targets come from mandatory rules). Test execution: `NOT APPLICABLE` at Phase 00. |
| **Phase** | 00 foundation → planned per phase (TST-01), executed in Phases 03–07 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Fix the testing obligations now so Phase 03's toolchain measures the right things and Phase
07 cannot retro-fit a strategy.

## 2. Scope

- **In:** test pyramid, mandatory per-function requirements, coverage targets, suite
  inventory, bug taxonomy, what "green" means.
- **Out:** test cases, fixtures, harness setup (Phases 03/04/07).

## 3. Current status

| Metric | Value |
|---|---|
| Test files | **0** |
| Test runner | not chosen (`NOT YET AVAILABLE — PHASE 00`) |
| Tests executed | 0 |
| Coverage | **not measurable** |
| CI | none (`F-012`) |

> Reporting `NOT APPLICABLE`, not `PASS`. See `RULES_HINTS.md` §3.

## 4. Test pyramid (`CONFIRMED` obligation per `core/06` §6.1)

| Level | Scope | Minimum per phase |
|---|---|---|
| Unit | Function/class | every new function: happy path + validation failure (+ authorization where applicable) |
| Component | UI component / module in isolation | every new UI component renders + interacts |
| Integration | Module → DB → external services | every new transaction/CRUD end-to-end through a real DB (test container) |
| System | Whole feature flows | every use case main flow |
| End-user / UAT | Real user scenarios | every use case alternate + exception flow scripted |
| Performance | Budgets | critical endpoints benchmarked |
| Security | `SEC` test cases | every permissions-matrix row + injection suite |

**Ratio guidance (adopted from Source A `12`):** roughly E2E 5–10%, integration 20–30%,
unit 60–70% — i.e. *for every 1 E2E test, ~10 integration and ~100 unit tests*.

## 5. Mandatory per-function requirements (`CONFIRMED`)

| ID | Requirement | Rule |
|---|---|---|
| `TST-R-01` | Every phase ships a **test plan + test cases** covering all levels above | `TST-01` |
| `TST-R-02` | Every implemented function has ≥ 1 happy-path, 1 validation-failure, and (where applicable) 1 authorization test | `TST-02` |
| `TST-R-03` | Regression suite runs on every change; a failure blocks the commit | `TST-03` |
| `TST-R-04` | Per-phase QA attributes file: correctness, reliability, usability, performance, security, maintainability, portability — each with metric + result | `TST-04` |
| `TST-R-05` | Every bug gets severity, root cause, fix **and a regression test** | `TST-05` |
| `DOD-03` | 100% of tests pass; **0 silently skipped** (a skip needs a tracked ticket reference) | `DOD-03` |
| `DOD-04` | Coverage **≥ 80%** overall, **100%** on critical paths | `DOD-04` |
| `DOD-05` | 0 dead buttons, links, routes, DB transactions — proven by **automated inventory test**, not inspection | `DOD-05` |

### Critical paths (100% coverage required)

Authentication · authorization · **payments / money movement** (fine payment) · core CRUD ·
data transactions · anything the security audit flags critical.

## 6. Suite inventory (`PROPOSED`)

| Suite | Purpose | Phase available |
|---|---|---|
| Unit | function/class behaviour | 03 |
| Component | UI rendering & interaction | 06 |
| Integration | DB + module + external service | 03–05 |
| Contract | API & event contracts (producer/consumer) | 02 planned, 05 executed |
| System / E2E | use-case flows | 04–06 |
| Dead-element inventory | UI registry ↔ route/handler registry diff | 06 |
| Performance / benchmark | p95 budgets | 07 |
| Security | permissions matrix rows + injection | 07 |
| Accessibility | axe / Lighthouse, WCAG 2.1 AA | 06–07 |

## 7. Bug taxonomy (`CONFIRMED` convention)

| Field | Values |
|---|---|
| Severity | `CRITICAL` / `HIGH` / `MEDIUM` / `LOW` (**canonical**) |
| Priority | `P0`–`P4` (P0 = immediate) |
| Required fields | severity, root cause, fix, regression test |
| Register location | the active phase's `AUDIT.md` findings table |

> Source A uses `Major/Minor/Observation` for audit findings and `P0`–`P4` for defects —
> both map onto the canonical severity taxonomy above.

## 8. Confirmed information

§4, §5 and §7 are `CONFIRMED` obligations derived from mandatory rules. **No test has been
written or run.**

## 9. Assumptions

| ID | Assumption |
|---|---|
| `AS-T-01` | A Node/TypeScript test runner will be chosen in Phase 03 |
| `AS-T-02` | Integration tests will use a real PostgreSQL in a test container |
| `AS-T-03` | The ≥ 80% / 100% coverage targets are accepted as-is (rule defaults) |

## 10. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-T-01` | Which test framework, assertion and mocking libraries? | 03 |
| `OQ-T-02` | Is CI required for grading, and on which platform? | 03 |
| `OQ-T-03` | Are performance targets confirmed (p95 ≤ 500/800 ms)? | 01/02 |
| `OQ-T-04` | Is formal UAT expected, and who performs it? | 07 |
| `OQ-T-05` | Must accessibility be proven with an automated tool? | 06/07 |

## 11. Traceability references

- **Upstream:** [`../senior-rules/RULES.md`](../senior-rules/RULES.md) (`TST-*`, `DOD-03`…`DOD-05`) ·
  [`02-use-cases.md`](02-use-cases.md) (flows → tests) ·
  [`03-use-case-actions.md`](03-use-case-actions.md) (action → ≥3 tests) ·
  [`12-security-specification.md`](12-security-specification.md) (security suite)
- **Downstream:** [`14-quality-attributes.md`](14-quality-attributes.md) (measured results) ·
  [`../phases/phase-07-quality-security/PLAN.md`](phases/phase-07-quality-security/PLAN.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 12. Related documents

- [`14-quality-attributes.md`](14-quality-attributes.md)
- [`12-security-specification.md`](12-security-specification.md)
- [`../senior-rules/core/06_quality_and_testing.md`](../senior-rules/core/06_quality_and_testing.md)
- [`../senior-rules/core/01_definition_of_done.md`](../senior-rules/core/01_definition_of_done.md)
