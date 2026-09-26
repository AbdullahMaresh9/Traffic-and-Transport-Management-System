# 06 — Data Flow

| Field | Value |
|---|---|
| **Purpose** | Show where data originates, how it moves between actors, processes, stores and external systems — including the database transactions each flow performs. |
| **Scope** | DFD conventions, boundary context and candidate data stores. Diagrams are drawn in Phase 01/02. |
| **Current Status** | Skeleton — **0 DFDs drawn**; conventions `CONFIRMED`, data stores `PROPOSED`. |
| **Phase** | 00 foundation → completed in Phase 01 (logical) / Phase 02 (physical) |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Satisfy the DFD requirement of `core/03` (artifact 6) and `core/10` §10.2 — *detailed data
flows including DB transactions, level 1 minimum for new features* — and give Phase 02's
database design a data-movement view to be validated against.

## 2. Scope

- **In:** notation, level convention, transaction rules, external boundary map, candidate
  data stores.
- **Out:** the diagrams themselves (Phase 01/02), schema/ERD (Phase 02 →
  [`09-database.md`](09-database.md)).

## 3. Current status

| Metric | Value |
|---|---|
| Context diagram (L0) | not drawn |
| Level-1 DFDs | **0 of N** |
| DB transactions mapped | 0 |
| Data stores identified | 8 (`PROPOSED`) |

## 4. Known context

- External systems are all `PROPOSED INTEGRATION BOUNDARY` — data flows crossing them are
  hypothetical (`../architecture.md` §4.3).
- ADMR requires multi-write operations to be atomic and represented in the DFD and state
  machine (`core/09` §9.2), and requires relational activity logging (`LOG-01`).

## 5. Notation & rules (`CONFIRMED` convention)

| Element | Notation |
|---|---|
| External entity | rectangle — actor or confirmed external system |
| Process | rounded rect — numbered `P<n>` / `P<n>.<m>` |
| Data store | open-ended rect — `D<n>: <name>` |
| Flow | labelled arrow |
| Diagram format | Mermaid inside this file (or the phase folder), linked from `architecture.md` |
| Required levels | L0 context + L1 minimum; L2 for any feature added later |

**Transaction rules**

1. Every flow that writes ≥ 2 stores must show an explicit transaction boundary.
2. Failure of any write must roll back completely (`core/09` §9.2).
3. Event emission must be transactional (outbox) — see [`05-flow-events.md`](05-flow-events.md) §5.
4. Every flow must show error/failure paths (IMP-05).

## 6. External boundary map (`PROPOSED INTEGRATION BOUNDARY` — none confirmed)

```
                 ┌──────────────────────────────┐
  Citizens ──────┤                              ├──── Civil Registry      [PROPOSED]
  Drivers  ──────┤                              ├──── Police / Emergency  [PROPOSED]
  Officers ──────┤   Traffic and Transport      ├──── Payment Gateway     [PROPOSED]
  Operators ─────┤   Management System          ├──── Notification Prov.  [PROPOSED]
  Analysts ──────┤   (L0 context)               ├──── GIS / Mapping       [PROPOSED]
  Admins ────────┤                              ├──── Sensor/Signal Sim.  [PROPOSED]
  Auditors ──────┘                              └──── (internal stores)
```

> No arrow crossing an external system may be treated as real until Phase 01 confirms it.

## 7. Candidate data stores (`PROPOSED`)

| ID | Data store | Owner domain | Notes |
|---|---|---|---|
| `D01` | Citizen / Driver | Driver Management | May be external (Civil Registry) — `OPEN QUESTION` |
| `D02` | Vehicle | Vehicle Management | |
| `D03` | License & Penalty Points | License Management | lifecycle-bearing → needs state machine |
| `D04` | Violation | Violation Management | lifecycle-bearing → needs state machine |
| `D05` | Fine & Payment | Violation / Payment | money-moving → critical path, 100% coverage |
| `D06` | Accident / Incident | Accident / Traffic | |
| `D07` | Monitoring & Signal observations | Traffic Monitoring | high volume? `OPEN QUESTION` |
| `D08` | Audit / Activity log | Audit | schema doctrine in `senior-rules/core/07` |
| `D09` | Identity (users, roles, permissions) | Identity & Access | schema doctrine in `core/05` §5.2 |

> These are **candidate** stores derived from `mindmap.md`, not a schema. Numbering, merging
> and splitting are decided in Phase 02.

## 8. Confirmed information

Notation and transaction rules in §5 are `CONFIRMED` conventions. **No data flow is
confirmed**; 0 diagrams exist.

## 9. Assumptions

| ID | Assumption |
|---|---|
| `AS-D-01` | A single relational database (PostgreSQL, `PROPOSED`) hosts all internal stores |
| `AS-D-02` | Monitoring observations may be high-volume relative to the rest |
| `AS-D-03` | Mermaid DFD notation is acceptable for submission |

## 10. Open questions

| ID | Question |
|---|---|
| `OQ-D-01` | What level of DFD does the supervisor expect (L0+L1, or L2 as well)? |
| `OQ-D-02` | Which data does TTMS own versus borrow from the Civil Registry? |
| `OQ-D-03` | What are the expected data volumes and retention periods? |
| `OQ-D-04` | Must every DB transaction be individually listed, or is diagram-level enough? |

## 11. Traceability references

- **Upstream:** [`04-flow-actions.md`](04-flow-actions.md) (persistence columns) ·
  [`05-flow-events.md`](05-flow-events.md) · [`../mindmap.md`](../mindmap.md)
- **Downstream:** [`09-database.md`](09-database.md) (schema) ·
  [`12-security-specification.md`](12-security-specification.md) (data classes) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 12. Related documents

- [`05-flow-events.md`](05-flow-events.md)
- [`09-database.md`](09-database.md)
- [`../architecture.md`](../architecture.md)
- [`../senior-rules/core/09_data_and_api.md`](../senior-rules/core/09_data_and_api.md)
