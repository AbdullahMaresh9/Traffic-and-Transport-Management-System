# Implementation Plan — phase-06-reporting-ui

- Phase: **PH-06 — UI / Dashboard / Reporting** · Slug: `phase-06-reporting-ui` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-04` (must be `PASSED`)
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Build the user-facing application: HCI-conformant UI, dashboards and reporting — every control wired to a real backend handler.

### Out of scope

Anything not derived from the approved requirements baseline (`SYS-03`). Phases 00–02 contain no application implementation (`SYS-01`, `SYS-08`).

## 2. Inputs

| Input | Status |
|---|---|
| Previous phase outputs | `CONFIRMED` prerequisite |
| Rule set + `../../../RULES_HINTS.md` | `CONFIRMED` prerequisite |
| `../../../architecture.md` | `CONFIRMED` prerequisite |

## 3. Outputs

| Output | Status |
|---|---|
| Implemented UI (screens, navigation, states) | `NOT STARTED` |
| Baselined `../../07-website-structure.md` and `../../08-ui-ux-specification.md` | `NOT STARTED` |
| `uiux-<phase>.md` records | `NOT STARTED` |
| Reusable confirmation modal | `NOT STARTED` |
| Component inventory test | `NOT STARTED` |
| Reporting views | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Baseline website structure and UI/UX specification | Design baseline | `../../07`, `../../08` | `NOT STARTED` |
| A2 | Implement screen structure, navigation and responsive layouts | Implementation | UI shell | `NOT STARTED` |
| A3 | Implement dashboards and reporting views | Implementation | dashboards | `NOT STARTED` |
| A4 | Wire every control to a real backend handler (`IMP-01`, `IMP-02`) | Implementation + scan | 0 dead elements | `NOT STARTED` |
| A5 | Replace native dialogs with a reusable confirmation modal; no alert/confirm/prompt | Implementation | modal | `NOT STARTED` |
| A6 | Externalize all user-facing strings | Implementation | i18n/resource files | `NOT STARTED` |
| A7 | Accessibility audit (WCAG 2.1 AA, axe/Lighthouse) | Audit | audit evidence | `NOT STARTED` |
| A8 | Run gates + validator, evaluate exit gate, commit | `GEN-04` + `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `IMP-01`/`IMP-02`: every visible control wired; zero dead elements.
- `IMP-03`: UI hiding is never a permission — enforcement stays server-side.
- Accessibility and responsiveness come from `../../14-quality-attributes.md`.

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| UI built before domain phase completes | `HIGH` | Dependency on Phase 04 |
| Accessibility retrofitted late | `MEDIUM` | Audit runs inside this phase, not at project end |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
