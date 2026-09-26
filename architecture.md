# architecture.md — Traffic and Transport Management System

> **Current status of everything on this page: `PROPOSED`.**
> Nothing here is approved. No ADR has been accepted yet. All architectural hypotheses
> below are validated (or rejected) during **Phase 02 — Architecture & Integration Design**
> and recorded as decision records in [`docs/decisions/`](docs/decisions/).
>
> Rules: `DOC-01`, `core/10_architecture.md` (C4 + DDD + ADR), `RULES_HINTS.md` SYS-06.

---

## 0. Document control

| Field | Value |
|---|---|
| Status | `PROPOSED` (Phase 00 skeleton) |
| Phase | 00 — Initialization & Governance |
| Last updated | 2026-09-26 |
| Validated in | Phase 02 (**not yet begun**) |
| ADRs accepted | **0** |
| Owner | `OPEN QUESTION` — no human architect assigned |

---

## 1. Architectural hypothesis

**MODULAR MONOLITH + INTEGRATION LAYER + EVENT-DRIVEN COMMUNICATION**

Rationale (`ASSUMPTION`): a modular monolith gives an academic project the clarity of a
single deployable while still demonstrating module boundaries, and an integration layer plus
a message broker demonstrates both synchronous and asynchronous integration concepts —
which is the core of the *Systems Integration and Architecture* course objective.

| Hypothesis element | Demonstrates |
|---|---|
| Modular monolith | Architecture & module boundaries, DDD-lite contexts |
| Integration layer + adapters | Systems integration, external-system isolation |
| Event-driven communication | Async contracts, broker topology, event consumers |

**Alternatives considered at this stage (not evaluated — deferred to Phase 02):**
microservices, event-carried state transfer with a monolith, serverless.
No trade-off analysis has been performed. `OPEN QUESTION`.

## 2. Proposed technology direction

All rows are `PROPOSED`. Selection method required by `core/03_phase_documentation.md` §
"Technology recommendation": a weighted Technology Evaluation Matrix in the Phase 02
implementation plan, with conformity checked against `RULES_HINTS.md` §2.

| Layer | Proposed choice | Status | Needs ADR? |
|---|---|---|---|
| Frontend | React + TypeScript | `PROPOSED` | yes |
| Backend | NestJS + TypeScript | `PROPOSED` | yes |
| Database | PostgreSQL | `PROPOSED` | yes |
| API | REST + OpenAPI | `PROPOSED` | yes |
| Messaging | RabbitMQ | `PROPOSED` | yes |
| Authentication | JWT + RBAC | `PROPOSED` | yes |
| Containerization | Docker / Docker Compose | `PROPOSED` | yes |

> **No code, manifest, lockfile, container or database exists.** This table describes intent
> only. See `RULES_HINTS.md` §3 for which tooling commands actually exist today.

## 3. Proposed structural model (C4 — placeholder)

`core/10_architecture.md` §10.1 requires C4 structural views. They are **not yet drawn**;
drawing them now would fabricate detail that Phase 01/02 must produce.

### 3.1 Context level (L0) — `PROPOSED`, undrawn

The system's candidate actors and candidate external systems are catalogued in
[`mindmap.md`](mindmap.md) and [`docs/11-integration-specification.md`](docs/11-integration-specification.md).
Each external system is a **`PROPOSED INTEGRATION BOUNDARY`** (SYS-04) — none is confirmed.

### 3.2 Container level (L1) — `PROPOSED`, undrawn

Expected containers (hypothesis only): web frontend, API application, relational database,
message broker. To be modelled in Phase 02.

### 3.3 Component level (L2) — `PROPOSED`, undrawn

Candidate module boundaries are listed in §5 below. To be modelled in Phase 02.

## 4. Proposed domain boundaries (initial map)

**Not automatically confirmed requirements.** Status of every row: `PROPOSED DOMAIN`.

### Core domain

| Boundary | Status |
|---|---|
| Traffic Management | `PROPOSED DOMAIN` |

### Supporting domains

| Boundary | Status |
|---|---|
| Driver Management | `PROPOSED DOMAIN` |
| Vehicle Management | `PROPOSED DOMAIN` |
| License Management | `PROPOSED DOMAIN` |
| Violation Management | `PROPOSED DOMAIN` |
| Accident Management | `PROPOSED DOMAIN` |
| Traffic Monitoring | `PROPOSED DOMAIN` |
| Traffic Signals | `PROPOSED DOMAIN` |
| Reporting | `PROPOSED DOMAIN` |
| Notifications | `PROPOSED DOMAIN` |
| Identity & Access | `PROPOSED DOMAIN` |
| Audit | `PROPOSED DOMAIN` |

### External systems — each a `PROPOSED INTEGRATION BOUNDARY`

| Candidate external system | Status | Confirmed by stakeholder? |
|---|---|---|
| Civil Registry | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |
| Police / Emergency | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |
| Payment Gateway | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |
| Notification Provider | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |
| GIS / Mapping | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |
| Traffic Sensor / Signal Simulator | `PROPOSED INTEGRATION BOUNDARY` | **No** — `OPEN QUESTION` |

> Whether these systems exist, are reachable, or are even in scope is **unknown**. Phase 01
> must resolve each one. Do not design adapters for them yet.

## 5. Proposed integration model

The system should eventually demonstrate **both** integration styles. Neither is
implemented, and neither is contractually specified yet.

### 5.1 Synchronous (`PROPOSED`)

- REST APIs with request/response contracts
- OpenAPI contract-first definition (per `skills/08_integration_ai` API-First workflow)

### 5.2 Asynchronous (`PROPOSED`)

- Domain events published to a message broker (RabbitMQ, `PROPOSED`)
- Event consumers with dead-letter handling

### 5.3 Candidate integration scenarios (`PROPOSED` — questions, not requirements)

| Candidate scenario | Style | Why it might be useful | Status |
|---|---|---|---|
| Citizen identity verification | sync | verify a driver/citizen against a registry | `PROPOSED` — depends on Civil Registry boundary |
| Payment of a traffic fine | sync (+async ack) | money movement through a gateway | `PROPOSED` — depends on Payment Gateway boundary |
| Accident notification | async | push accident events to emergency services | `PROPOSED` — depends on Police/Emergency boundary |
| Traffic notification | async | notify citizens of incidents/congestion | `PROPOSED` — depends on Notification Provider boundary |
| Traffic sensor events | async | ingest readings from sensors/signal simulator | `PROPOSED` — depends on Sensor/Signal Simulator boundary |

**Do not implement any of these in Phase 00.** `RULES_HINTS.md` SYS-01.

## 6. Architecture decisions

| ADR | Title | Status |
|---|---|---|
| — | *(none yet)* | — |

Accepted decisions live in [`docs/decisions/`](docs/decisions/). Until an ADR reaches
`Accepted`, the corresponding choice remains `PROPOSED`. Do not silently convert an
assumption into a fact (`GEN-03`, SYS-06).

## 7. Architecture delta log

`core/10_architecture.md` §10.1 requires every phase to append an architecture delta to
this file — never a divergent side file.

| Phase | Delta | Date | ADR |
|---|---|---|---|
| 00 | File created; hypothesis + proposed stack + proposed boundaries recorded as `PROPOSED` | 2026-09-26 | none |

## 8. Open architecture questions

| ID | Question | Status |
|---|---|---|
| `AQ-01` | Is a modular monolith the right style, or does the course require demonstrating microservices? | `OPEN QUESTION` |
| `AQ-02` | Are the six candidate external systems real, reachable, and in scope? | `OPEN QUESTION` |
| `AQ-03` | Is RabbitMQ necessary, or is an in-process/event-sourced alternative sufficient for an academic demo? | `OPEN QUESTION` |
| `AQ-04` | Which C4 diagrams, state machines, sequence and activity diagrams does the supervisor expect, and how detailed? | `OPEN QUESTION` |
| `AQ-05` | What non-functional targets are actually required (concurrency, uptime, response times)? | `OPEN QUESTION` |
| `AQ-06` | Single-locale `en` only, or multi-locale/RTL support? | `OPEN QUESTION` (see `RULES_HINTS.md` §6) |
| `AQ-07` | Who is the human architect/owner that signs off architecture? | `OPEN QUESTION` |

## 9. Related documents

- [`mindmap.md`](mindmap.md) — full conceptual hierarchy with status labels
- [`docs/01-requirements.md`](docs/01-requirements.md) — requirements foundation
- [`docs/09-database.md`](docs/09-database.md) — database architecture foundation
- [`docs/10-api-specification.md`](docs/10-api-specification.md) — API foundation
- [`docs/11-integration-specification.md`](docs/11-integration-specification.md) — integration foundation
- [`docs/12-security-specification.md`](docs/12-security-specification.md) — security architecture foundation
- [`docs/14-quality-attributes.md`](docs/14-quality-attributes.md) — quality attributes
- [`docs/15-risk-register.md`](docs/15-risk-register.md) — architecture/technical risks
- [`docs/decisions/`](docs/decisions/) — ADRs
- [`memory.md`](memory.md) — current architecture hypothesis (cumulative)
- [`RULES_HINTS.md`](RULES_HINTS.md) — the `PROPOSED` stack binding
