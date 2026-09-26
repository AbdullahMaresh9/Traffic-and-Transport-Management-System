# Task Todo — Phase 03: Technical Foundation

> Status: **`NOT STARTED`** — this phase has not begun; every box is unchecked (`GEN-02`).
> Dependencies: `PH-02` (must be `PASSED`) must be `PASSED` first.
> Phase ID: `PH-03` · Slug: `phase-03-foundation` · Phase state: `PH-00` `PASSED` · `PH-01` `NOT STARTED` (`../../../ENTRY.md`)

---

## A. Preparation

- [ ] Confirm Phase 02 gate `PASSED`
- [ ] Load `parallel-execution` skill
- [ ] Define repository structure

## B. Toolchain

- [ ] Build/lint/test/coverage tooling
- [ ] CI pipeline
- [ ] Migration tooling + rollback rehearsal
- [ ] Secret + dependency scanning
- [ ] Docker base
- [ ] Auth skeleton

## C. Validation & closure

- [ ] Run gates G1–G7 with raw output
- [ ] Run validator with raw output
- [ ] Update `../../../RULES_HINTS.md` §3 (same commit)
- [ ] Evaluate exit gate
- [ ] Write `AUDIT.md`, session log, commit

---

## Exit-gate checklist (evaluate with evidence at closure)

| # | Check | Status |
|---|---|---|
| 1 | Build: 0 errors | `NOT STARTED` |
| 2 | Lint clean | `NOT STARTED` |
| 3 | Test harness green | `NOT STARTED` |
| 4 | Coverage measuring ≥ 80% | `NOT STARTED` |
| 5 | Secret scan and dependency scan runnable and clean | `NOT STARTED` |
| 6 | Migration rollback rehearsed | `NOT STARTED` |
| 7 | `../../../RULES_HINTS.md` §3 updated in the same commit | `NOT STARTED` |
| 8 | First phase where gates G1–G7 become executable — all executed with raw output | `NOT STARTED` |
| 9 | Validator green (raw output recorded) | `NOT STARTED` |

**Phase status:** `NOT STARTED`. Do not mark any item complete without pasted evidence (`GEN-04`).

---

## Roll-up

- Plan: [`PLAN.md`](PLAN.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Registry: [`../../../development_phases_entry.md`](../../../development_phases_entry.md)
