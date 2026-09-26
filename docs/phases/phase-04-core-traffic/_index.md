# Phase 04 — Core Traffic Domain

**Phase ID:** `PH-04` · **Slug:** `phase-04-core-traffic` · **Status:** `NOT STARTED` · **Registry:** [`../../../development_phases_entry.md`](../../../development_phases_entry.md)

## Objective

Implement the core traffic domain and its supporting domains end-to-end: drivers, vehicles, licenses, violations, fines, penalty points, accidents, incidents, monitoring, signals, reporting and notifications.

## Key facts

| Field | Value |
|---|---|
| Phase ID | `PH-04` |
| Slug | `phase-04-core-traffic` |
| Status | `NOT STARTED` |
| Dependencies | `PH-03` (must be `PASSED`) |
| Owner | AI agent; human sign-off **`BLOCKED` (`F-006`)** |
| Gate | see [`AUDIT.md`](AUDIT.md) §5 |

## Deliverables

- Implemented core domain (backend + data layer)
- Full CORE-03 artifact set (use cases, DFD, state machines, sequence/activity diagrams, test plan, permissions matrix, QA file, security audit)
- State machines for every lifecycle-bearing entity
- Tests: happy path + validation + authorization per function

## Files in this phase folder

| File | Purpose |
|---|---|
| [`TODO.md`](TODO.md) | Task checklist + exit-gate table |
| [`PLAN.md`](PLAN.md) | Objective, inputs/outputs, activities, risks, rules |
| [`AUDIT.md`](AUDIT.md) | Findings register, gate evaluation, validation evidence |
| [`_index.md`](_index.md) | This index |

---

**Next:** start only when every dependency phase is `PASSED` with evidence.

Related: [`../README.md`](../README.md) · [`../../../ENTRY.md`](../../../ENTRY.md) · [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md) · [`../../../memory.md`](../../../memory.md)
