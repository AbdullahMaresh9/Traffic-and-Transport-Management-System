# 05 — Flow of Events

| Field | Value |
|---|---|
| **Purpose** | Capture the **asynchronous** side of the system: domain events, their producers, consumers, ordering, idempotency and failure handling. |
| **Scope** | Event conventions and a candidate event register. The event catalogue itself is produced in Phase 01/02. |
| **Current Status** | Skeleton — **0 confirmed events**; 16 candidate events `PROPOSED`. |
| **Phase** | 00 foundation → completed in Phase 01 (identification) / Phase 02 (design) |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Event-driven communication is one of the project's explicit objectives. This document fixes
how events are named, modelled, delivered and verified in this project — so that the
asynchronous integration demonstrated in Phase 05 is coherent rather than ad hoc.

## 2. Scope

- **In:** event conventions, candidate event register, delivery guarantees, failure policy.
- **Out:** broker topology, exchange/queue naming, retry/backoff parameters (Phase 02, in
  [`11-integration-specification.md`](11-integration-specification.md)); event implementations (Phase 05).

## 3. Current status

| Metric | Value |
|---|---|
| Candidate events listed | 16 |
| `CONFIRMED` | **0** |
| Consumers specified | 0 |
| Broker chosen | `PROPOSED` — RabbitMQ |

## 4. Known context

- The proposed integration model is **both** synchronous (REST) and asynchronous
  (domain events over a broker) — see [`../architecture.md`](../architecture.md) §5.
- `core/09` §9.2 requires multi-write operations to be atomic and represented in the phase
  DFD and state machine.
- `senior-rules` doctrine requires a dead-letter pattern (`core/06`/`08` in Source A;
  `LOG-03` fail-safe logging in ADMR).

## 5. Event conventions (`CONFIRMED` as convention; content `PROPOSED`)

| Convention | Rule |
|---|---|
| Naming | Past-tense, `<Aggregate><Event>` — e.g. `ViolationRecorded`, `FinePaid` |
| Payload | Minimal, self-describing, **no PII beyond what the consumer needs** (LOG-02) |
| Versioning | Every event carries a schema version; breaking change = new version (IMP-07) |
| Producer | Exactly one aggregate owns each event |
| Delivery | At-least-once → **consumers must be idempotent** |
| Ordering | Per-aggregate ordering only; no global ordering assumed |
| Failure | Non-retryable failures → dead-letter queue with alert; never block the business transaction (LOG-03) |
| Correlation | Every event carries a correlation ID for session reconstruction (LOG-04) |
| Outbox | Events emitted transactionally with the state change (transactional outbox) |
| Testing | Contract tests per producer/consumer pair; failure-injection test for DLQ |

## 6. Candidate event register (`PROPOSED` — none confirmed)

| Event ID | Event | Producer (aggregate) | Candidate consumer(s) | Integration purpose | Status |
|---|---|---|---|---|---|
| `EV-01` | `CitizenVerified` | Identity | driver/license service | Citizen identity verification (sync-confirmed, async-ack) | `PROPOSED` |
| `EV-02` | `DriverRegistered` | Driver | license service, reporting | — | `PROPOSED` |
| `EV-03` | `VehicleRegistered` | Vehicle | monitoring, reporting | — | `PROPOSED` |
| `EV-04` | `LicenseIssued` | License | driver, notifications | — | `PROPOSED` |
| `EV-05` | `LicenseSuspended` | License | driver, notifications, enforcement | — | `PROPOSED` |
| `EV-06` | `ViolationRecorded` | Violation | fine service, penalty service, reporting | — | `PROPOSED` |
| `EV-07` | `ViolationContested` | Violation | enforcement, reporting | — | `PROPOSED` |
| `EV-08` | `FineIssued` | Fine | notifications, payment | — | `PROPOSED` |
| `EV-09` | `FinePaid` | Fine | reporting, notifications | Payment of traffic fine (async ack) | `PROPOSED` |
| `EV-10` | `PenaltyPointsAwarded` | License | license, driver | — | `PROPOSED` |
| `EV-11` | `AccidentReported` | Accident | police/emergency, monitoring, notifications | Accident notification | `PROPOSED` — boundary unconfirmed |
| `EV-12` | `IncidentReported` | Traffic Incident | monitoring, notifications | Traffic notification | `PROPOSED` — boundary unconfirmed |
| `EV-13` | `CongestionDetected` | Monitoring | reporting, notifications | Traffic notification | `PROPOSED` |
| `EV-14` | `SensorReadingReceived` | Monitoring | monitoring | Traffic sensor events | `PROPOSED` — boundary unconfirmed |
| `EV-15` | `SignalStateChanged` | Signals | monitoring | Traffic sensor/signal events | `PROPOSED` — boundary unconfirmed |
| `EV-16` | `NotificationDelivered` | Notifications | audit | — | `PROPOSED` |

> **Nothing above is a requirement or a confirmed design.** Four events depend on external
> boundaries that are themselves unconfirmed (`Audit.md` `F-005`).

## 7. Candidate scenarios mapped to the brief (`PROPOSED`)

| Brief scenario | Style | Events |
|---|---|---|
| Citizen identity verification | synchronous primary | `EV-01` |
| Payment of traffic fine | synchronous primary, async ack | `EV-09`, `EV-08` |
| Accident notification | asynchronous | `EV-11` |
| Traffic notification | asynchronous | `EV-12`, `EV-13` |
| Traffic sensor events | asynchronous | `EV-14`, `EV-15` |

## 8. Confirmed information

Conventions in §5 are `CONFIRMED` as project conventions (governance-level decisions, not
business requirements). **0 confirmed events.**

## 9. Assumptions

| ID | Assumption |
|---|---|
| `AS-E-01` | At-least-once delivery + idempotent consumers is the right guarantee for this system |
| `AS-E-02` | A transactional outbox is acceptable complexity for an academic demonstration |
| `AS-E-03` | Domain events map 1:1 onto broker messages (no separate integration-event translation) |

## 10. Open questions

| ID | Question |
|---|---|
| `OQ-E-01` | Which of the 16 events are actually needed? |
| `OQ-E-02` | Is RabbitMQ required by the course, or would an in-process bus suffice? (`AQ-03`) |
| `OQ-E-03` | What is the event schema format (Avro / JSON Schema / plain TS types)? |
| `OQ-E-04` | Must ordering, retry counts and DLQ policy be specified for grading? |
| `OQ-E-05` | Are events expected to cross a trust boundary (i.e. to real external systems)? (`OQ-02`) |

## 11. Traceability references

- **Upstream:** [`02-use-cases.md`](02-use-cases.md) (`UC-` producing events) ·
  [`04-flow-actions.md`](04-flow-actions.md) (steps that emit) ·
  [`../architecture.md`](../architecture.md) §5.2
- **Downstream:** [`06-data-flow.md`](06-data-flow.md) ·
  [`11-integration-specification.md`](11-integration-specification.md) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (contract + failure-injection tests) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 12. Related documents

- [`04-flow-actions.md`](04-flow-actions.md)
- [`06-data-flow.md`](06-data-flow.md)
- [`11-integration-specification.md`](11-integration-specification.md)
- [`../architecture.md`](../architecture.md)
