# 09 — Database Specification (Architecture Foundation)

| Field | Value |
|---|---|
| **Purpose** | Capture what is currently known about the data architecture, the questions that must be answered, and the constraints the eventual schema must satisfy. |
| **Scope** | Foundation only — known context, questions, initial proposed structure, constraints, validation needs. **Not** a schema. |
| **Current Status** | `PROPOSED` foundation. **No tables, columns, migrations or ERD exist or are specified.** |
| **Phase** | 00 foundation → fully specified in **Phase 02** |
| **Last updated** | 2026-09-26 |

> Detailed schema design, ERD, indexing, and the migration strategy belong to Phase 02.
> This file must not be treated as a database design.

---

## 1. Purpose

Give Phase 02 a constrained starting point: what is already known, what is decided by rule,
and what remains genuinely open.

## 2. Scope

- **In:** storage-engine hypothesis, candidate entities, rule-imposed schema requirements,
  open data questions, validation plan.
- **Out:** tables/columns/types/indexes/constraints, ERD, migration scripts (Phase 02/03).

## 3. Known context

| Item | Value |
|---|---|
| Proposed engine | PostgreSQL (`PROPOSED`) |
| ORM / query layer | `OPEN QUESTION` — not chosen |
| Migration tool | `OPEN QUESTION` — not chosen |
| Migrations existing | **0** |
| Tables existing | **0** |
| Candidate data stores | 8–9 (`PROPOSED`) — see [`06-data-flow.md`](06-data-flow.md) §7 |

## 4. Initial proposed structure (`PROPOSED` — not a schema)

Aggregate/entity **candidates** derived from `mindmap.md`. Each is a *name*, not a design.

| Candidate aggregate | Lifecycle-bearing? | Notes |
|---|---|---|
| Citizen / Driver | no | may be owned by the external Civil Registry (`OQ-D-02`) |
| Vehicle | no | |
| License | **yes** | needs state machine (issued / expiring / suspended / revoked) |
| Violation | **yes** | needs state machine (recorded / contested / upheld / void) |
| Fine / Payment | **yes** | money-moving → critical path → 100% coverage (`DOD-04`) |
| Penalty Points | **yes** | derived; threshold-driven suspension |
| Accident | **yes** | report lifecycle |
| Traffic Incident | **yes** | `OPEN QUESTION` vs. Accident (`OQ-05`) |
| Traffic Signal / Signal observation | **yes** | signal state |
| Monitoring observation | no | potentially high volume (`AS-D-02`) |
| Road | `OPEN QUESTION` | own model or GIS-provided? (`MQ-04`) |
| User / Role / Permission | no | RBAC model unknown (`OQ-06`) |
| Audit / Activity log | no | relational schema doctrine exists (see §5) |

## 5. Rule-imposed requirements (`CONFIRMED` as obligations)

These come from the mandatory rules and constrain whatever design Phase 02 produces:

| ID | Requirement | Rule |
|---|---|---|
| `DB-R-01` | Every schema change ships a **versioned migration + rollback script**; rollback is *rehearsed*, not theoretical | `IMP-06`, `core/09` §9.1 |
| `DB-R-02` | Destructive changes require backup confirmation + expand/contract note | `core/09` §9.1 |
| `DB-R-03` | Multi-write operations are atomic; failure rolls back completely | `core/09` §9.2 |
| `DB-R-04` | Every transaction appears in the DFD and the entity's state machine | `core/09` §9.2 |
| `DB-R-05` | Parameterized queries / ORM bindings **only** — never string-concatenated SQL | `core/05` §5.3, `SEC-03` |
| `DB-R-06` | Activity logging uses the relational schema doctrine: `users`, `user_sessions`, `actions`, `errors`, `activity_stats` — each with timestamp, actor FK, session FK, correlation ID, result status | `LOG-01`, `core/07` §7.1 |
| `DB-R-07` | PII redaction and secret scrubbing **before** persistence; documented retention & access control | `LOG-02` |
| `DB-R-08` | Log writes are fail-safe: a logging failure must never break the business transaction | `LOG-03` |
| `DB-R-09` | Sensitive data encrypted at rest; referential integrity enforced | `SEC-08` |
| `DB-R-10` | Backups automated and restore-tested, with RPO/RTO documented | `SEC-09` — **currently `OPEN QUESTION`** |

## 6. Constraints

| Constraint | Status |
|---|---|
| Engine is `PROPOSED` until a Phase 02 ADR accepts it | `PROPOSED` |
| No schema may be created during Phase 00 (`SYS-01`) | `CONFIRMED` |
| Data volumes, growth and retention are unknown | `OPEN QUESTION` |
| Which data TTMS owns vs. borrows is unknown | `OPEN QUESTION` |
| No RPO/RTO target defined | `OPEN QUESTION` |

## 7. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-DB-01` | PostgreSQL confirmed, or must alternatives be evaluated? (`AQ-01`) | 02 |
| `OQ-DB-02` | Which ORM/query builder? | 02 |
| `OQ-DB-03` | Which migration tool, and how is rollback rehearsed? | 02/03 |
| `OQ-DB-04` | Which entities does TTMS own versus the Civil Registry? (`OQ-D-02`) | 01 |
| `OQ-DB-05` | Expected volumes and retention periods? (`OQ-D-03`) | 01 |
| `OQ-DB-06` | Is audit-log retention fixed (rule suggests ≥ 1 year in Source A; ADMR leaves it to policy)? | 01/02 |
| `OQ-DB-07` | Multi-tenancy or single-deployment? | 02 |
| `OQ-DB-08` | Are there reporting queries requiring special structures (views, materialized views)? | 01/02 |

## 8. Validation needs (Phase 02 exit criteria for this document)

- [ ] Every `CONFIRMED` requirement traces to at least one entity (`SYS-05`)
- [ ] Every lifecycle-bearing aggregate has a documented state machine
- [ ] ERD produced and reviewed; all candidate aggregates resolved or rejected
- [ ] Migration + rollback chosen and the rollback **rehearsed** (evidence)
- [ ] `DB-R-01`…`DB-R-10` each have a concrete implementation plan
- [ ] Open questions `OQ-DB-01`…`OQ-DB-08` resolved or explicitly deferred with an owner
- [ ] Architecture review passed

## 9. Traceability references

- **Upstream:** [`../mindmap.md`](../mindmap.md) concepts · [`06-data-flow.md`](06-data-flow.md) stores ·
  [`01-requirements.md`](01-requirements.md) categories
- **Downstream:** [`10-api-specification.md`](10-api-specification.md) (operations over entities) ·
  [`12-security-specification.md`](12-security-specification.md) (data classes, encryption) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (transaction/integration tests) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 10. Related documents

- [`06-data-flow.md`](06-data-flow.md)
- [`10-api-specification.md`](10-api-specification.md)
- [`12-security-specification.md`](12-security-specification.md)
- [`../architecture.md`](../architecture.md)
- [`../phases/phase-02-architecture/PLAN.md`](phases/phase-02-architecture/PLAN.md)
