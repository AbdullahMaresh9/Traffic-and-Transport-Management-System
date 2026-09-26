# Task Todo — Phase 05: External System Integration

> Status: **`NOT STARTED`** — this phase has not begun; every box is unchecked (`GEN-02`).
> Dependencies: `PH-04` (must be `PASSED`) must be `PASSED` first.
> Phase ID: `PH-05` · Slug: `phase-05-integration` · Active phase: `PH-00` (`../../../ENTRY.md`)

---

## A. Preparation

- [ ] Confirm Phase 04 gate `PASSED`
- [ ] Confirm external-system list (F-005)
- [ ] Re-read `../../11-integration-specification.md`

## B. Integration

- [ ] Sync REST contracts
- [ ] Async events over the broker
- [ ] Adapters for confirmed systems only
- [ ] Contract tests
- [ ] Idempotency + dead-letter handling
- [ ] Failure-path tests

## C. Validation & closure

- [ ] Run gates with raw output
- [ ] Run validator with raw output
- [ ] Evaluate exit gate
- [ ] Write `AUDIT.md`, session log, commit

---

## Exit-gate checklist (evaluate with evidence at closure)

| # | Check | Status |
|---|---|---|
| 1 | Contract tests green for every confirmed boundary | `NOT STARTED` |
| 2 | Event consumers idempotent and dead-lettered | `NOT STARTED` |
| 3 | Failure paths tested | `NOT STARTED` |
| 4 | No adapter built for an unconfirmed boundary (`SYS-04`) | `NOT STARTED` |
| 5 | 0 open `CRITICAL`/`HIGH` findings | `NOT STARTED` |
| 6 | Validator green (raw output recorded) | `NOT STARTED` |

**Phase status:** `NOT STARTED`. Do not mark any item complete without pasted evidence (`GEN-04`).

---

## Roll-up

- Plan: [`PLAN.md`](PLAN.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Registry: [`../../../development_phases_entry.md`](../../../development_phases_entry.md)
