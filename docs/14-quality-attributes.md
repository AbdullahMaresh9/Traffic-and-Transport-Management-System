# 14 — Quality Attributes

| Field | Value |
|---|---|
| **Purpose** | Define the system's quality attributes as **measurable scenarios**, so "good quality" becomes verifiable rather than subjective. |
| **Scope** | Attribute catalogue, scenario format, current targets and their status. **No measurement possible yet.** |
| **Current Status** | `PROPOSED` — targets are rule defaults or `OPEN QUESTION`; **0 measurements taken**. |
| **Phase** | 00 foundation → quantified in Phase 01/02, measured in Phase 07 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

`TST-04` requires a QA attributes file per phase with metric + result, and Source A's
quality-attribute scenario format makes an NFR testable. This document fixes the format and
the candidate targets now.

## 2. Scope

- **In:** ISO 25010-aligned attribute set, scenario format, candidate targets + status.
- **Out:** measured results (Phase 07), acceptance of targets (Phase 01/02).

## 3. Scenario format (`CONFIRMED` convention)

From Source A `05` §"Quality Attribute Scenario template":

> **Source / Stimulus / Environment / Artifact / Response / Response Measure**

Every confirmed NFR must be expressible in this form. A statement without a *Response
Measure* is not verifiable — and "a requirement that cannot be tested is not a requirement".

## 4. Quality attributes (`PROPOSED` — none confirmed by a stakeholder)

| Attribute | Candidate scenario (abbreviated) | Target | Status | Measured |
|---|---|---|---|---|
| **Correctness** | system processes a valid operation as specified | 0 incorrect results | `CONFIRMED` (rule) | — |
| **Performance** | user requests a read under normal load | p95 ≤ **500 ms** | `PROPOSED` (rule default, not stakeholder-confirmed) | not measurable |
| **Performance** | user submits a write | p95 ≤ **800 ms** | `PROPOSED` (rule default) | not measurable |
| **Performance** | page becomes interactive on throttled 4G | ≤ **3 s**; TTFB ≤ **600 ms** | `PROPOSED` (rule default) | not measurable |
| **Performance** | first-load bundle size | ≤ **250 KB** gzipped | `PROPOSED` (rule default) | not measurable |
| **Reliability** | component failure under normal operation | availability target **`OPEN QUESTION`** | `OPEN QUESTION` | — |
| **Scalability** | concurrent users / data volume | **`OPEN QUESTION`** | `OPEN QUESTION` (`OQ-07`) | — |
| **Security** | unauthorized access attempt | denied server-side, logged | `CONFIRMED` (rule `SEC-02`) | — |
| **Security** | security audit findings | **0 `CRITICAL`/`HIGH`**, 0 secrets | `CONFIRMED` (rule `DOD-06`) | — |
| **Usability** | completing a core task unaided | **`OPEN QUESTION`** (SUS target?) | `OPEN QUESTION` | — |
| **Accessibility** | keyboard-only + screen-reader path for critical flows | **WCAG 2.1 AA**, axe = 0 serious | `PROPOSED` (rule `UI-02`) | not measurable |
| **Maintainability** | change a behaviour | automated tests detect regression | `CONFIRMED` (rule `TST-03`) | — |
| **Testability / coverage** | automated coverage measurement | ≥ **80%** overall, **100%** critical paths | `CONFIRMED` (rule `DOD-04`) | not measurable |
| **Portability / deployability** | run the system locally | Docker Compose up from a clean checkout | `PROPOSED` | — |
| **Auditability** | reconstruct any user session from logs | full reconstruction possible | `CONFIRMED` (rule `LOG-04`) | — |
| **Internationalization** | render a locale | **`OPEN QUESTION`** (locale set unknown) | `OPEN QUESTION` (`OQ-08`) | — |
| **Observability** | logging pipeline failure | business transaction still succeeds | `CONFIRMED` (rule `LOG-03`) | — |

## 5. Confirmed information

Targets marked `CONFIRMED` are **rule obligations**, not stakeholder requirements. The
distinction matters: a rule default may be tightened freely and loosened only with user
approval (`RULES_HINTS.md` §6).

## 6. Assumptions

| ID | Assumption |
|---|---|
| `AS-Q-01` | Rule-default performance budgets are a reasonable baseline for this system |
| `AS-Q-02` | ISO 25010 is the expected quality model (Source A `05`) |
| `AS-Q-03` | Single-node local deployment is the target environment, so availability targets are low-stakes |

## 7. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-Q-01` | Which performance budgets does the supervisor actually require? (`OQ-07`) | 01/02 |
| `OQ-Q-02` | Is an availability/reliability target required? | 01/02 |
| `OQ-Q-03` | What concurrency/data volume must be supported? | 01 |
| `OQ-Q-04` | Is a formal usability target (SUS score) expected? | 01 |
| `OQ-Q-05` | Which quality attributes are graded, and with what weight? | 01 |

## 8. Validation needs

- [ ] Every `OPEN QUESTION` target resolved or explicitly marked `NOT APPLICABLE` with a reason
- [ ] Each confirmed attribute expressed as a full scenario with a Response Measure
- [ ] Rule defaults either accepted or tightened (never silently loosened) — user approval required to loosen
- [ ] Measurement commands available (`RULES_HINTS.md` §3) before any `Measured` column is filled
- [ ] Phase 07 fills the `Measured` column with raw output, not narrative

## 9. Traceability references

- **Upstream:** [`01-requirements.md`](01-requirements.md) §7 (`NFR-CAT-01`…`10`) ·
  [`../senior-rules/core/01_definition_of_done.md`](../senior-rules/core/01_definition_of_done.md) (`DOD-07`)
- **Downstream:** [`13-testing-strategy.md`](13-testing-strategy.md) (how measured) ·
  [`15-risk-register.md`](15-risk-register.md) (unquantified targets are risks) ·
  [`../phases/phase-07-quality-security/PLAN.md`](phases/phase-07-quality-security/PLAN.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 10. Related documents

- [`01-requirements.md`](01-requirements.md)
- [`13-testing-strategy.md`](13-testing-strategy.md)
- [`15-risk-register.md`](15-risk-register.md)
- [`../RULES_HINTS.md`](../RULES_HINTS.md) §6 (overrides)
