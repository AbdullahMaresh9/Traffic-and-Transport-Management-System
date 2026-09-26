# 11 — Integration Specification (Architecture Foundation)

| Field | Value |
|---|---|
| **Purpose** | Record the proposed integration model, the candidate external systems, the questions each boundary raises, and what must be validated before any adapter is designed. |
| **Scope** | Foundation only — boundaries, styles, scenarios, constraints, validation needs. **No adapter or contract is specified.** |
| **Current Status** | `PROPOSED` foundation. **6 candidate boundaries, 0 confirmed, 0 adapters, 0 contracts.** |
| **Phase** | 00 foundation → designed in Phase 02, implemented in Phase 05 |
| **Last updated** | 2026-09-26 |

> Every external system listed here is a **`PROPOSED INTEGRATION BOUNDARY`** (`SYS-04`).
> Designing an adapter for an unconfirmed boundary would be fabrication.

---

## 1. Purpose

Systems integration is the course's core objective, so the integration *questions* must be
framed early — while the *answers* wait for Phase 01/02 evidence.

## 2. Scope

- **In:** integration styles, candidate boundaries, candidate scenarios, mandatory
  integration rules, validation needs.
- **Out:** adapter design, protocol/endpoint/contract detail, broker topology (Phase 02),
  implementation (Phase 05).

## 3. Known context

| Item | Value |
|---|---|
| Required to demonstrate | **both** synchronous and asynchronous integration (`CONFIRMED` objective) |
| Sync style | REST request/response (`PROPOSED`) |
| Async style | domain events over RabbitMQ (`PROPOSED`) |
| Candidate boundaries | 6 (table §4) — **all unconfirmed** |
| Adapters implemented | 0 |
| Contract tests | 0 |

## 4. Candidate integration boundaries (`PROPOSED INTEGRATION BOUNDARY`)

| ID | Candidate system | Purpose (hypothesised) | Likely style | Confirmed? | Blocking questions |
|---|---|---|---|---|---|
| `EXT-01` | Civil Registry | verify citizen/driver identity; possibly license issuance | sync | **No** | exists? reachable? owns which data? (`OQ-UC-01`, `OQ-D-02`) |
| `EXT-02` | Police / Emergency | accident & incident notification | async (or sync push) | **No** | exists? protocol? required by whom? |
| `EXT-03` | Payment Gateway | traffic fine payment | sync | **No** | exists? real or simulated? (`OQ-R-06`) |
| `EXT-04` | Notification Provider | deliver notifications | sync | **No** | channels? provider? (`FR-CAT-12`) |
| `EXT-05` | GIS / Mapping | roads, locations, geocoding | sync | **No** | needed at all? owns the Road model? (`MQ-04`) |
| `EXT-06` | Traffic Sensor / Signal Simulator | sensor events, signal state | async | **No** | real hardware available? simulator acceptable? (`OQ-12`) |

**Status summary:** 0 of 6 confirmed. Tracked as `Audit.md` `F-005` (`HIGH`).

## 5. Candidate scenarios from the brief (`PROPOSED`)

| Scenario | Style | Boundary | Notes |
|---|---|---|---|
| Citizen identity verification | synchronous REST | `EXT-01` | |
| Payment of traffic fine | synchronous REST (+ async ack) | `EXT-03` | money-moving → critical path |
| Accident notification | asynchronous event | `EXT-02` | |
| Traffic notification | asynchronous event | `EXT-04` | |
| Traffic sensor events | asynchronous event | `EXT-06` | |

## 6. Mandatory integration rules (`CONFIRMED` as obligations)

| ID | Requirement | Rule |
|---|---|---|
| `INT-R-01` | API-first: contract defined **before** implementation, mocked, implemented, validated by contract tests | Source A `08` §3.1 (adopted as guidance) |
| `INT-R-02` | APIs are contracts — breaking them breaks trust; no silent breakage | `IMP-07` |
| `INT-R-03` | Every integration point has explicit timeout, retry, and failure handling (IMP-05) | `IMP-05` |
| `INT-R-04` | Idempotency keys for anything that can be delivered twice; replay prevention (timestamp/signature validation) | Source A `08` webhook rules |
| `INT-R-05` | Dead-letter handling for failed event processing; logging failure must never break business flow | `LOG-03` |
| `INT-R-06` | Inbound data validated at the trust boundary; parameterized queries only | `SEC-03` |
| `INT-R-07` | Security headers / CORS allowlist / rate limiting on exposed surfaces | `SEC-07` |
| `INT-R-08` | Integration security audit per phase; 0 open `CRITICAL`/`HIGH` at phase close | `SEC-04` |
| `INT-R-09` | No adapter built for an unconfirmed boundary | `SYS-04` |

## 7. Constraints

| Constraint | Status |
|---|---|
| Both sync and async must be demonstrated | `CONFIRMED` (objective) |
| No external system confirmed | `BLOCKED` (`F-005`) |
| Broker choice is `PROPOSED` | `PROPOSED` (`AQ-03`) |
| No adapter, contract or simulator may be built during Phase 00 (`SYS-01`) | `CONFIRMED` |
| Real hardware (sensors/signals) availability unknown | `OPEN QUESTION` |

## 8. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-INT-01` | Which of the 6 boundaries are real, reachable and in scope? | 01 |
| `OQ-INT-02` | Are simulators acceptable substitutes for real systems? (`OQ-12`) | 01 |
| `OQ-INT-03` | Which protocols/versions do real systems use (REST? SOAP? MQTT? file feed?)? | 02 |
| `OQ-INT-04` | Is RabbitMQ confirmed, or is a lighter broker/in-process bus acceptable? (`AQ-03`) | 02 |
| `OQ-INT-05` | Must failure/retry/timeout behaviour be demonstrated as well as the happy path? | 01/02 |
| `OQ-INT-06` | Are external calls mocked entirely, or is at least one real integration expected? | 01 |
| `OQ-INT-07` | Who owns data quality at each boundary? | 01/02 |

## 9. Validation needs (Phase 02 exit criteria for this document)

- [ ] Each boundary in §4 either **confirmed** (with evidence: reachable endpoint, contract,
      owner) or explicitly removed from scope with rationale
- [ ] `Audit.md` `F-005` closed or re-scoped
- [ ] Both a sync and an async path chosen for demonstration, with named scenarios
- [ ] Adapter pattern, protocol, error model and retry policy decided per confirmed boundary
- [ ] Broker decision recorded as an ADR
- [ ] Contract-test strategy recorded in [`13-testing-strategy.md`](13-testing-strategy.md)
- [ ] Threat model covers every trust boundary crossed (`SEC-04`)

## 10. Traceability references

- **Upstream:** [`../architecture.md`](../architecture.md) §4.3–§5 ·
  [`02-use-cases.md`](02-use-cases.md) (`UC-12`, `UC-23`, `UC-24`) ·
  [`05-flow-events.md`](05-flow-events.md) (`EV-*`)
- **Downstream:** [`10-api-specification.md`](10-api-specification.md) (external contracts) ·
  [`12-security-specification.md`](12-security-specification.md) (trust boundaries) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (contract & failure tests) ·
  [`15-risk-register.md`](15-risk-register.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 11. Related documents

- [`../architecture.md`](../architecture.md)
- [`05-flow-events.md`](05-flow-events.md)
- [`10-api-specification.md`](10-api-specification.md)
- [`12-security-specification.md`](12-security-specification.md)
- [`../phases/phase-05-integration/PLAN.md`](phases/phase-05-integration/PLAN.md)
