# Phase 03 — Technical Foundation

**Phase ID:** `PH-03` · **Slug:** `phase-03-foundation` · **Status:** `NOT STARTED` · **Registry:** [`../../../development_phases_entry.md`](../../../development_phases_entry.md)

## Objective

Create the toolchain and skeleton that later phases build on: repository structure, CI, lint/test/coverage tooling, migration tooling, secret and dependency scanning, Docker base, auth skeleton.

## Key facts

| Field | Value |
|---|---|
| Phase ID | `PH-03` |
| Slug | `phase-03-foundation` |
| Status | `NOT STARTED` |
| Dependencies | `PH-02` (must be `PASSED`) |
| Owner | AI agent; human sign-off **`BLOCKED` (`F-006`)** |
| Gate | see [`AUDIT.md`](AUDIT.md) §5 |

## Deliverables

- Repository structure
- CI pipeline
- Lint/test/coverage tooling
- Migration tooling + rollback rehearsal evidence
- Secret + dependency scanning (closes `F-012`)
- Docker base
- Auth skeleton
- Implemented commands in `../../../RULES_HINTS.md` §3
- `permissions-<feature>.md`

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
