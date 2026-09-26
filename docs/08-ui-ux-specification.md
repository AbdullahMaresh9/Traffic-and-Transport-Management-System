# 08 — UI / UX Specification

| Field | Value |
|---|---|
| **Purpose** | Hold the HCI, usability, accessibility and interaction rules that the eventual UI must satisfy. |
| **Scope** | Requirements-level only. No visual design, no mockups, no components exist yet. |
| **Current Status** | Skeleton — rules `PROPOSED` (drawn from mandatory UI rules), user research **absent**. |
| **Phase** | 00 foundation → specified in Phase 02, verified in Phase 06 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Fix the quality bar for the UI *before* any UI is built, so Phase 06 cannot discover an
accessibility requirement too late.

## 2. Scope

- **In:** usability heuristics, accessibility target, interaction patterns, i18n rules,
  responsive rules, error-message standards.
- **Out:** wireframes, visual design, design tokens, component implementation
  (Phase 06); page inventory (→ [`07-website-structure.md`](07-website-structure.md)).

## 3. Current status

| Metric | Value |
|---|---|
| User personas | **0 — none created** (no user research available) |
| Usability tests run | 0 |
| Mockups | 0 |
| Components built | 0 |
| Accessibility audit | not possible (no UI) |

## 4. Known context

- Actors and users are unconfirmed, so no persona-driven design is possible yet.
- Mandatory UI rules are already in force regardless: `UI-01`…`UI-04`, `IMP-01`…`IMP-05`,
  `DOD-05`.

## 5. Interaction rules (`PROPOSED` — from mandatory rules)

| Rule | Requirement | Source |
|---|---|---|
| Confirmation pattern | `alert()`, `confirm()`, `prompt()` are **forbidden**. One reusable confirmation modal: title, message, consequence warning, confirm/cancel, keyboard accessible, focus-trapped, ARIA-dialog. | `IMP-04`, `core/08` §8.1 |
| Error handling | Every operation handles success, validation failure, server error and network error — no unhandled branches. | `IMP-05` |
| Dead elements | Every button/link/action rendered maps to a wired handler → real backend route. | `IMP-01`, `IMP-02`, `DOD-05` |
| Heuristics | Phase with UI ships `uiux-<phase>.md`: heuristics review, task effort, error-message quality, consistency audit. | `UI-01` |
| Confirmation modal tests | The modal itself has unit + accessibility tests. | `core/08` §8.1 |

## 6. Accessibility target (`PROPOSED`, rule-mandated)

**Target: WCAG 2.1 AA** (`UI-02`). Required checks once UI exists:

- keyboard-only navigation pass
- visible focus management
- contrast ≥ 4.5:1
- labelled controls, screen-reader path for critical flows
- automated axe / Lighthouse audit = **0 serious violations**

> Status today: `NOT APPLICABLE` — no UI to audit. Not a pass.

## 7. Internationalization & responsiveness

| Aspect | Rule | Status |
|---|---|---|
| Hardcoded strings | none permitted | rule `CONFIRMED` |
| Locales | `OPEN QUESTION` — default assumption single `en` (`AS-R-02`, `OQ-08`) | **unresolved** |
| RTL | `OPEN QUESTION` — depends on locale answer | **unresolved** |
| Breakpoints | supported-breakpoint matrix tested visually per phase (`UI-04`) | targets unknown (`OQ-W-04`) |

## 8. Confirmed information

Nothing about users is confirmed. The interaction and accessibility *rules* in §5–§6 are
`CONFIRMED` as mandatory rule obligations.

## 9. Assumptions

| ID | Assumption |
|---|---|
| `AS-U-01` | A single design language across all role views |
| `AS-U-02` | Web is the only channel |
| `AS-U-03` | WCAG 2.1 AA is acceptable to the supervisor (it is a rule default, not a stakeholder requirement) |

## 10. Open questions

| ID | Question |
|---|---|
| `OQ-U-01` | Who are the users, and what are their tasks? (blocks all persona work) |
| `OQ-U-02` | Is there a required visual identity / brand / colour palette? |
| `OQ-U-03` | Is a design system or component library prescribed? |
| `OQ-U-04` | Must the UI be demonstrated live for grading, and on which devices? |
| `OQ-U-05` | Are dashboards expected to be interactive (filters, drill-down) or static? |

## 11. Traceability references

- **Upstream:** [`01-requirements.md`](01-requirements.md) §4–§5, §7 (`NFR-CAT-05/06/09`) ·
  [`07-website-structure.md`](07-website-structure.md)
- **Downstream:** [`13-testing-strategy.md`](13-testing-strategy.md) (accessibility test suite) ·
  [`14-quality-attributes.md`](14-quality-attributes.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 12. Related documents

- [`07-website-structure.md`](07-website-structure.md)
- [`13-testing-strategy.md`](13-testing-strategy.md)
- [`14-quality-attributes.md`](14-quality-attributes.md)
- [`../senior-rules/core/08_ui_ux.md`](../senior-rules/core/08_ui_ux.md)
