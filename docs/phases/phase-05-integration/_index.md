# Phase 05 — External System Integration

**Phase ID:** `PH-05` · **Slug:** `phase-05-integration` · **Status:** `NOT STARTED` · **Registry:** [`../../../development_phases_entry.md`](../../../development_phases_entry.md)

## Objective

Demonstrate both integration styles: synchronous REST contracts and asynchronous domain events over the broker, through adapters for whichever external systems were confirmed in Phase 01.

## Key facts

| Field | Value |
|---|---|
| Phase ID | `PH-05` |
| Slug | `phase-05-integration` |
| Status | `NOT STARTED` |
| Dependencies | `PH-04` (must be `PASSED`) |
| Owner | AI agent; human sign-off **`BLOCKED` (`F-006`)** |
| Gate | see [`AUDIT.md`](AUDIT.md) §5 |

## Deliverables

- Adapter implementations for confirmed boundaries only
- Contract tests
- Dead-letter handling evidence
- Integration security audit
- Phase audit + session evidence

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
