# 04 — Flow of Actions

| Field | Value |
|---|---|
| **Purpose** | Sequence the actions from [`03-use-case-actions.md`](03-use-case-actions.md) into main, alternate and exception flows — the narrative view of *how* each use case proceeds. |
| **Scope** | Flow structure, notation and conventions. Individual flows are written in Phase 01. |
| **Current Status** | Skeleton — **0 flows written**; conventions `CONFIRMED`, examples `PROPOSED`. |
| **Phase** | 00 foundation → completed in Phase 01 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Provide the canonical way a flow is written in this project, so that flows produced by
different sessions (or different agents) are structurally identical and reviewable.

## 2. Scope

- **In:** required flow sections, notation, naming, one worked `PROPOSED` example.
- **Out:** the flows themselves (Phase 01), state machines (also Phase 01/04), event flows
  (see [`05-flow-events.md`](05-flow-events.md)).

## 3. Current status

| Metric | Value |
|---|---|
| Use cases needing flows | 24 |
| Main flows written | **0** |
| Alternate flows written | **0** |
| Exception flows written | **0** |

## 4. Known context

`core/03_phase_documentation.md` requires, for specification-type artifacts: purpose,
scope, actors/roles, preconditions, main flow, alternate flows, exception flows,
postconditions, data entities touched, invariants, and open questions — with diagrams as
Mermaid inside the markdown file. This document fixes that contract for this project.

## 5. Required structure for every flow (`CONFIRMED` convention)

```
### <UC-ID> — <Use case title>

- Status: CONFIRMED | PROPOSED | OPEN QUESTION | BLOCKED
- Primary actor: …        Secondary actors: …
- Precondition(s): …
- Trigger: …

#### Main flow
1. <action ID> — <imperative step>
2. …

#### Alternate flows
A1. <condition> → <divergent steps>

#### Exception flows
E1. <failure> → <recovery / abort steps>   (must cover: validation failure,
   unauthorized, server error, network error — IMP-05)

#### Postcondition(s)
- On success: …
- On failure: … (unchanged)

#### Data entities touched
| Entity | Read/Write | Transaction | Notes |

#### Invariants
- … (conditions that always hold)

#### Open questions
- OQ-…: …
```

## 6. Worked example (`PROPOSED` — illustrative only)

```
### UC-08 — Pay a traffic fine

- Status: PROPOSED (use case unconfirmed — see 02-use-cases.md)
- Primary actor: ACT-01 Citizen
- Precondition(s): fine exists, is unpaid, and belongs to the actor
- Trigger: actor submits payment

#### Main flow
1. ACT-UC08-01 Submit payment intent for fine F
2. ACT-UC08-02 Validate fine exists and is unpaid
3. ACT-UC08-03 Authorize with payment gateway
4. ACT-UC08-04 Record payment result
5. ACT-UC08-05 Publish FinePaid domain event
6. ACT-UC08-06 Send payment confirmation notification

#### Exception flows
E1. Gateway unreachable → record pending state, offer retry, do NOT mark fine paid
E2. Gateway declines   → record failed attempt, fine remains unpaid

#### Data entities touched
| Entity     | R/W | Transaction            |
|------------|-----|------------------------|
| fine       | R   | read-only              |
| payment    | W   | atomic with fine state  |

#### Open questions
OQ-R-06: payment gateway boundary is unconfirmed (Audit.md F-005)
```

> **Illustrative, not a requirement.** Nothing in this example is confirmed.

## 7. Confirmed information

The structure in §5 is `CONFIRMED` as this project's convention (it derives directly from
`core/03` §"Content standards"). **No flow content is confirmed.**

## 8. Assumptions

| ID | Assumption |
|---|---|
| `AS-F-01` | Mermaid-in-markdown is acceptable to the supervisor instead of a separate diagram tool (`OQ-04`) |
| `AS-F-02` | One flow document per phase is sufficient; flows live here rather than duplicated into phase folders |

## 9. Open questions

| ID | Question |
|---|---|
| `OQ-F-01` | Which use cases require flows first? (prioritisation pending `OQ-UC-04`) |
| `OQ-F-02` | Are activity diagrams with swimlanes required in addition to these flows? (`core/10` §10.2 says yes — confirm expectation and detail level) |
| `OQ-F-03` | Must flows include the state transition triggered at each step? |

## 10. Traceability references

- **Upstream:** [`03-use-case-actions.md`](03-use-case-actions.md) (action IDs) ·
  [`02-use-cases.md`](02-use-cases.md) (`UC-` IDs)
- **Downstream:** [`05-flow-events.md`](05-flow-events.md) (event-producing steps) ·
  [`06-data-flow.md`](06-data-flow.md) (entity/transaction steps) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 11. Related documents

- [`03-use-case-actions.md`](03-use-case-actions.md)
- [`05-flow-events.md`](05-flow-events.md)
- [`06-data-flow.md`](06-data-flow.md)
- [`../senior-rules/core/03_phase_documentation.md`](../senior-rules/core/03_phase_documentation.md)
