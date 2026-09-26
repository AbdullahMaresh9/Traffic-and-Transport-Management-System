# docs/phases — Phase Index

| Field | Value |
|---|---|
| **Purpose** | Link every phase folder and its artifacts, forming the roll-up required by `DOC-04`. |
| **Scope** | Index only — no phase content lives here. |
| **Current Status** | All 9 phase folders exist with `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`. Only Phase 00 has content. |
| **Phase** | 00 |
| **Last updated** | 2026-09-26 |

> Roll-up chain (**mandatory**, checked by `DOC-04`):
> phase artifacts → **this index** → [`../../development_phases_entry.md`](../../development_phases_entry.md)
> → [`../../all_in_one_track.md`](../../all_in_one_track.md).

---

## Phase folders

| Phase | Folder | Status | Index |
|---|---|---|---|
| 00 | [`phase-00-initialization/`](phase-00-initialization/_index.md) | **`ACTIVE`** — exit gate `BLOCKED` | [`_index.md`](phase-00-initialization/_index.md) |
| 01 | [`phase-01-analysis/`](phase-01-analysis/_index.md) | `NOT STARTED` ← next | [`_index.md`](phase-01-analysis/_index.md) |
| 02 | [`phase-02-architecture/`](phase-02-architecture/_index.md) | `NOT STARTED` | [`_index.md`](phase-02-architecture/_index.md) |
| 03 | [`phase-03-foundation/`](phase-03-foundation/_index.md) | `NOT STARTED` | [`_index.md`](phase-03-foundation/_index.md) |
| 04 | [`phase-04-core-traffic/`](phase-04-core-traffic/_index.md) | `NOT STARTED` | [`_index.md`](phase-04-core-traffic/_index.md) |
| 05 | [`phase-05-integration/`](phase-05-integration/_index.md) | `NOT STARTED` | [`_index.md`](phase-05-integration/_index.md) |
| 06 | [`phase-06-reporting-ui/`](phase-06-reporting-ui/_index.md) | `NOT STARTED` | [`_index.md`](phase-06-reporting-ui/_index.md) |
| 07 | [`phase-07-quality-security/`](phase-07-quality-security/_index.md) | `NOT STARTED` | [`_index.md`](phase-07-quality-security/_index.md) |
| 08 | [`phase-08-final-delivery/`](phase-08-final-delivery/_index.md) | `NOT STARTED` | [`_index.md`](phase-08-final-delivery/_index.md) |

---

## What every phase folder must contain

| # | Artifact | Template | Phase 00 status |
|---|---|---|---|
| 1 | Implementation plan (`PLAN.md`) | `senior-rules/templates/TEMPLATE_phase_implementation_plan.md` | `CREATED` |
| 2 | Task todo (`TODO.md`) | `senior-rules/templates/TEMPLATE_task_todo.md` | `CREATED` |
| 3 | Architecture delta | merged into `../../architecture.md` §7 | `CREATED` (delta recorded) |
| 4 | Use case file | section spec in `senior-rules/core/03_phase_documentation.md` | `NOT APPLICABLE` (no functionality) |
| 5 | Use case descriptions + flows | same | `NOT APPLICABLE` |
| 6 | Data flow diagram | same | `NOT APPLICABLE` |
| 7 | Non-functional requirements | same | `NOT APPLICABLE` (foundation in `../14-quality-attributes.md`) |
| 8 | QA file | same | `PARTIAL` — gate table in `AUDIT.md` |
| 9 | Security audit | `SEC-04` | `CREATED` (scoped honestly in `AUDIT.md` §4) |
| 10 | State machine(s) | same | `NOT APPLICABLE` (no entities) |
| 11 | Sequence diagram | separate file | `NOT APPLICABLE` |
| 12 | Activity diagram | separate file | `NOT APPLICABLE` |
| 13 | UI/UX specification | same | `NOT APPLICABLE` (foundation in `../08-ui-ux-specification.md`) |
| 14 | Test plan + cases | `senior-rules/templates/TEMPLATE_test_plan.md` | `NOT APPLICABLE` (no code) |
| 15 | Permissions/roles matrix | `senior-rules/templates/TEMPLATE_permissions_matrix.md` | `NOT APPLICABLE` (roles unknown) |
| 16 | Phase audit (`AUDIT.md`) | `senior-rules/templates/TEMPLATE_phase_audit.md` | `CREATED` |

> `NOT APPLICABLE` items are recorded **with a reason** in each phase's `_index.md` — never
> silently omitted (`DOD-08` / `DOC-02`).

---

## Related documents

- [`../../development_phases_entry.md`](../../development_phases_entry.md) — authoritative registry
- [`../../all_in_one_track.md`](../../all_in_one_track.md) — timeline roll-up
- [`../../Audit.md`](../../Audit.md) — findings across phases
- [`../sessions/`](../sessions/) — session evidence
