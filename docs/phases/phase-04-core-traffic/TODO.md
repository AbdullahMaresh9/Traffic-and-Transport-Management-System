# Task Todo — Phase 04: Core Traffic Domain

> Status: **`NOT STARTED`** — this phase has not begun; every box is unchecked (`GEN-02`).
> Dependencies: `PH-03` (must be `PASSED`) must be `PASSED` first.
> Phase ID: `PH-04` · Slug: `phase-04-core-traffic` · Active phase: `PH-00` (`../../../ENTRY.md`)

---

## A. Preparation

- [ ] Confirm Phase 03 gate `PASSED`
- [ ] Load `traffic-domain` + `parallel-execution` skills
- [ ] Re-read approved design (`../../09`, `../../10`)

## B. Domain build

- [ ] Data schema + migrations
- [ ] Driver/vehicle/license
- [ ] Violation/fine/penalty points
- [ ] Accident/incident/monitoring/signals
- [ ] Reporting/notifications
- [ ] Server-side authorization + validation per function

## C. Documentation

- [ ] CORE-03 artifact set
- [ ] State machines per entity
- [ ] Permissions matrix

## D. Validation & closure

- [ ] Run gates G1–G9 with raw output
- [ ] Dead-element scan
- [ ] Run validator with raw output
- [ ] Evaluate exit gate
- [ ] Write `AUDIT.md`, session log, commit

---

## Exit-gate checklist (evaluate with evidence at closure)

| # | Check | Status |
|---|---|---|
| 1 | All gates G1–G9 green (raw output) | `NOT STARTED` |
| 2 | 0 dead elements (`IMP-02`) | `NOT STARTED` |
| 3 | 0 open `CRITICAL`/`HIGH` findings | `NOT STARTED` |
| 4 | Every function has happy-path + validation + authorization tests | `NOT STARTED` |
| 5 | Permissions enforced server-side with tests (`IMP-03`) | `NOT STARTED` |
| 6 | State machines exist for every lifecycle-bearing entity | `NOT STARTED` |
| 7 | Validator green (raw output recorded) | `NOT STARTED` |

**Phase status:** `NOT STARTED`. Do not mark any item complete without pasted evidence (`GEN-04`).

---

## Roll-up

- Plan: [`PLAN.md`](PLAN.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Registry: [`../../../development_phases_entry.md`](../../../development_phases_entry.md)
