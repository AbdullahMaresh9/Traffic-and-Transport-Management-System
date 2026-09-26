# 02 — Use Cases

| Field | Value |
|---|---|
| **Purpose** | Hold the system's use-case inventory: what the system does, for whom, and at what confidence level. |
| **Scope** | Use-case **identification** only. Full descriptions (main/alternate/exception flows) are written in Phase 01. |
| **Current Status** | Skeleton — **0 use cases confirmed**; all candidates `PROPOSED`. |
| **Phase** | 00 foundation → baselined in Phase 01 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Provide a single place where candidate use cases are listed, linked to their functional
categories and actors, and tracked from `PROPOSED` → `CONFIRMED` → specified.

## 2. Scope

- **In:** candidate use-case titles, primary actor, linked `FR-CAT`, status, and the file
  where the detailed flow will live.
- **Out:** flow detail, acceptance criteria, business rules, pre/post-conditions — these are
  Phase 01 deliverables (`03-use-case-actions.md`, `04-flow-actions.md`, `05-flow-events.md`).

## 3. Current status

| Metric | Value |
|---|---|
| Candidate use cases listed | 24 |
| `CONFIRMED` | **0** |
| `PROPOSED` | 24 |
| Detailed descriptions written | 0 |

## 4. Known context

Derived from [`../mindmap.md`](../mindmap.md) and the functional categories in
[`01-requirements.md`](01-requirements.md) §6. Every candidate is a *plausible* use case for
a traffic-management system — **none has been validated with a stakeholder**, and none is an
approved requirement.

## 5. Candidate use-case inventory (`PROPOSED`)

| ID | Use case | Primary actor | FR-CAT | Status |
|---|---|---|---|---|
| `UC-01` | Register a citizen/driver record | `ACT-06` admin | `FR-CAT-04` | `PROPOSED` |
| `UC-02` | Register a vehicle | `ACT-06` admin | `FR-CAT-05` | `PROPOSED` |
| `UC-03` | Issue a driving license | `ACT-06` admin | `FR-CAT-06` | `PROPOSED` |
| `UC-04` | Renew / expire a driving license | `ACT-06` admin | `FR-CAT-06` | `PROPOSED` |
| `UC-05` | Record a traffic violation | `ACT-03` officer | `FR-CAT-07` | `PROPOSED` |
| `UC-06` | Adjudicate / contest a violation | `ACT-06` admin | `FR-CAT-07` | `PROPOSED` |
| `UC-07` | Calculate a fine for a violation | *system* | `FR-CAT-08` | `PROPOSED` |
| `UC-08` | Pay a traffic fine | `ACT-01` citizen | `FR-CAT-08` | `PROPOSED` |
| `UC-09` | Award penalty points | *system* | `FR-CAT-09` | `PROPOSED` |
| `UC-10` | Suspend / reinstate a license on threshold | *system* / `ACT-06` | `FR-CAT-09` | `PROPOSED` |
| `UC-11` | Report an accident | `ACT-03` officer | `FR-CAT-10` | `PROPOSED` |
| `UC-12` | Notify emergency services of an accident | *system* | `FR-CAT-10`, `FR-CAT-15` | `PROPOSED` |
| `UC-13` | Report a traffic incident | `ACT-04` operator | `FR-CAT-01` | `PROPOSED` |
| `UC-14` | Observe traffic sensor readings | *system* | `FR-CAT-02`, `FR-CAT-15` | `PROPOSED` |
| `UC-15` | Detect / report congestion | *system* | `FR-CAT-02` | `PROPOSED` |
| `UC-16` | Monitor traffic signal state | `ACT-04` operator | `FR-CAT-03` | `PROPOSED` |
| `UC-17` | Send a notification to a citizen | *system* | `FR-CAT-12`, `FR-CAT-15` | `PROPOSED` |
| `UC-18` | Log in / authenticate | all human actors | `FR-CAT-13` | `PROPOSED` |
| `UC-19` | Manage users, roles and permissions | `ACT-06` admin | `FR-CAT-13` | `PROPOSED` |
| `UC-20` | View the audit trail | `ACT-07` auditor | `FR-CAT-14` | `PROPOSED` |
| `UC-21` | Generate a traffic/management report | `ACT-05` analyst | `FR-CAT-11` | `PROPOSED` |
| `UC-22` | View a dashboard | `ACT-04` / `ACT-05` | `FR-CAT-11`, `FR-CAT-02` | `PROPOSED` |
| `UC-23` | Verify citizen identity against an external registry | *system* | `FR-CAT-15` | `PROPOSED` — depends on unconfirmed boundary |
| `UC-24` | Ingest traffic signal/sensor events | *system* | `FR-CAT-15` | `PROPOSED` — depends on unconfirmed boundary |

> **Explicitly not implied:** that all 24 will be implemented, that the actor assignments are
> correct, or that any named external system exists.

## 6. Confirmed information

None. There are **0 `CONFIRMED` use cases** at Phase 00.

## 7. Assumptions

| ID | Assumption |
|---|---|
| `AS-UC-01` | The `PROPOSED` actor assignments in §5 are a reasonable starting point for elicitation |
| `AS-UC-02` | `*system*`-initiated use cases are legitimate (event-triggered), not all user-initiated |

## 8. Open questions

| ID | Question |
|---|---|
| `OQ-UC-01` | Are `UC-01`/`UC-02`/`UC-03` actually performed *by this system*, or does it only consume registry data? (depends on the Civil Registry boundary) |
| `OQ-UC-02` | Is `UC-06` (contest a violation) in scope at all? |
| `OQ-UC-03` | Is `UC-10` automatic, or does it require human approval? |
| `OQ-UC-04` | Which of the 24 are `Must have` for the deliverable? |
| `OQ-UC-05` | Is there a "record a violation manually vs. sensor-detected" distinction? |

## 9. Relevant tables / diagrams

No diagram is drawn at Phase 00 — a use-case diagram would assert actors and boundaries that
are unconfirmed. The diagram is a Phase 01 deliverable.

## 10. Traceability references

- **Upstream:** [`01-requirements.md`](01-requirements.md) §6 `FR-CAT` ·
  [`../mindmap.md`](../mindmap.md) concepts
- **Downstream:** [`03-use-case-actions.md`](03-use-case-actions.md) (actions per use case) ·
  [`04-flow-actions.md`](04-flow-actions.md) · [`05-flow-events.md`](05-flow-events.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 11. Related documents

- [`03-use-case-actions.md`](03-use-case-actions.md)
- [`04-flow-actions.md`](04-flow-actions.md)
- [`05-flow-events.md`](05-flow-events.md)
- [`06-data-flow.md`](06-data-flow.md)
- [`16-glossary.md`](16-glossary.md)
