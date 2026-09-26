# 03 — Use Case Actions

| Field | Value |
|---|---|
| **Purpose** | Decompose each use case into its discrete actions, so that actions — not whole use cases — become the unit that maps to API operations, permissions and tests. |
| **Scope** | Action-level decomposition skeleton. Detailed descriptions (preconditions, main/alternate/exception flow, postconditions) belong to Phase 01. |
| **Current Status** | Skeleton — **0 actions confirmed**; the structure and method are established, examples are `PROPOSED`. |
| **Phase** | 00 foundation → completed in Phase 01 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Make every action of every use case explicit and individually addressable, so that:

- each action can later be traced to exactly one API operation (`SYS-05`),
- each action carries its own permission decision (IMP-03),
- each action gets its own tests (TST-02: happy path + validation failure + authorization).

## 2. Scope

- **In:** action inventory schema, decomposition method, worked `PROPOSED` examples.
- **Out:** full use-case specifications, flow narratives, state machines (see
  [`04-flow-actions.md`](04-flow-actions.md), [`05-flow-events.md`](05-flow-events.md)).

## 3. Current status

| Metric | Value |
|---|---|
| Use cases eligible for decomposition | 24 (see [`02-use-cases.md`](02-use-cases.md)) |
| Use cases decomposed | **0** |
| Actions specified | **0** |
| Actions confirmed | **0** |

## 4. Known context

Actions are not yet decomposed because the use cases themselves are `PROPOSED`. Decomposing
them now would produce a large volume of plausible-but-unverified detail.

## 5. Method (adopted, in force)

For each use case, enumerate:

1. **Trigger** — who/what starts it
2. **Actor actions** — what the human or system does, one per line
3. **System actions** — validation, authorization, computation, persistence, notification
4. **External interactions** — calls to a `PROPOSED INTEGRATION BOUNDARY`
5. **For each action record:**

| Column | Meaning |
|---|---|
| Action ID | `ACT-<UC>-<NN>` (stable, never reused) |
| Action | Imperative, single, testable verb phrase |
| Actor | Who initiates |
| Authorization | Role(s) allowed — must map to a permissions-matrix row |
| Input | Data consumed, with validation rule |
| Output / effect | Data produced or state changed |
| Persistence | Which entities/transactions are written |
| Failure paths | Validation failure, unauthorized, server error, network error (IMP-05) |
| Status | `CONFIRMED` / `PROPOSED` / `OPEN QUESTION` / `BLOCKED` |

## 6. Worked example (`PROPOSED` — illustrative only)

Use case `UC-08` — *Pay a traffic fine* (itself `PROPOSED`):

| Action ID | Action | Actor | Authorization | Persistence | Status |
|---|---|---|---|---|---|
| `ACT-UC08-01` | Submit payment intent for fine F | `ACT-01` citizen | citizen owns fine | `payment` (pending) | `PROPOSED` |
| `ACT-UC08-02` | Validate fine exists and is unpaid | system | — | read | `PROPOSED` |
| `ACT-UC08-03` | Authorize with payment gateway | system | service credential | read (external) | `BLOCKED` — boundary unconfirmed (`F-005`) |
| `ACT-UC08-04` | Record payment result | system | — | `payment` (final) | `PROPOSED` |
| `ACT-UC08-05` | Publish `FinePaid` domain event | system | — | outbox | `PROPOSED` |
| `ACT-UC08-06` | Send payment confirmation notification | system | — | `notification` | `PROPOSED` |

> This example is **illustrative of the method, not a requirement.** `UC-08` and every action
> inside it remain `PROPOSED`.

## 7. Confirmed information

None. **0 confirmed actions.**

## 8. Assumptions

| ID | Assumption |
|---|---|
| `AS-A-01` | Action-level decomposition is the right granularity for API/permission/test mapping |
| `AS-A-02` | Money-moving actions will qualify as critical paths (100% coverage per DOD-04) — *only if* fine payment is in scope |

## 9. Open questions

| ID | Question |
|---|---|
| `OQ-A-01` | Does the supervisor expect this level of action decomposition, or standard use-case specifications only? (`OQ-04` in `architecture.md`) |
| `OQ-A-02` | Are system actions (validation/persistence) expected to be enumerated explicitly? |
| `OQ-A-03` | Which use cases are prioritised, so decomposition effort is not wasted? (`OQ-UC-04`) |

## 10. Traceability references

- **Upstream:** [`02-use-cases.md`](02-use-cases.md) (`UC-` IDs) ·
  [`01-requirements.md`](01-requirements.md) (`FR-CAT`)
- **Downstream:** [`04-flow-actions.md`](04-flow-actions.md) (action sequencing) ·
  [`10-api-specification.md`](10-api-specification.md) (one action → one operation) ·
  [`12-security-specification.md`](12-security-specification.md) (authorization column) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (one action → ≥3 tests) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 11. Related documents

- [`02-use-cases.md`](02-use-cases.md)
- [`04-flow-actions.md`](04-flow-actions.md)
- [`05-flow-events.md`](05-flow-events.md)
- [`10-api-specification.md`](10-api-specification.md)
- [`13-testing-strategy.md`](13-testing-strategy.md)
