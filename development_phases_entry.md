# development_phases_entry.md — Official Phase Registry

> **Authoritative source for: which phase is active, what it must produce, and exactly what
> its exit gate requires.** Every session reads this (protocol step 3).
>
> Governing rules: `DOC-02`, `DOC-04`, `AUD-04`, `core/03_phase_documentation.md`.
> Phase structure per project specification §13.

---

## 0. How to read this registry

| Field | Meaning |
|---|---|
| **Status** | `NOT STARTED` · `ACTIVE` · `BLOCKED` · `GATE REVIEW` · `PASSED` · `FAILED` |
| **Dependencies** | Phases that must be `PASSED` before this one may start |
| **Required artifacts** | Minimum set; every phase also carries `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md` |
| **Exit gate** | The verifiable conditions that must all hold before `Status = PASSED` |

**Gate decision vocabulary:** `GO` · `CONDITIONAL GO` · `NO-GO`.
A phase is `PASSED` only on `GO`, with evidence linked from its `AUDIT.md`.

**Feature-based phase trap (anti-pattern `AP-06`):** the roadmap is **not**
"Phase 1 = Violations, Phase 2 = Licensing, Phase 3 = Vehicles". Those are *domains*, and
they are handled inside Phase 04. The primary phases are the SDLC phases below.

---

## PHASE 00 — Initialization & Governance

| Field | Value |
|---|---|
| **Phase ID** | `PH-00` |
| **Slug** | `phase-00-initialization` |
| **Objective** | Establish repository, governance, documentation architecture, AI skills, rules integration, phase/session tracking, and the requirements/architecture analysis foundations — **without** any business implementation. |
| **Status** | **`PASSED`** (`GO`, 41/41 — reconciled 2026-09-26; see its `AUDIT.md` for the verified gate table) |
| **Dependencies** | none |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; root governance set; `docs/` skeleton; `.opencode/`; `senior-rules/`; `RULES_HINTS.md`; traceability structure |
| **Exit gate** | All 41 checks in `docs/phases/phase-00-initialization/AUDIT.md` §5 evaluated as `PASS` / `NOT APPLICABLE` with evidence; **no unresolved `CRITICAL`/`HIGH` findings applicable to Phase 00** (project-level phase-scope interpretation; deferred future-phase findings allowed if they carry target phase · owner · rationale · required-by gate · re-evaluation trigger) |
| **Completion state** | **100% — `PASSED`.** Exit gate `GO` after the 2026-09-26 reconciliation: `F-004`/`BLK-01` `FIXED` (verbatim appendix restored into `memory.md`), and `F-005`/`F-006`/`F-012` (`HIGH`) classified **`DEFERRED BY PHASE DESIGN`** with target phase, owner, rationale and required-by gate (root `Audit.md` §3.1) — open, visible, not applicable to Phase 00. Never reported as `READY`. |
| **Explicitly out of scope** | All business functionality (`RULES_HINTS.md` SYS-01) |

---

## PHASE 01 — Requirements & Domain Analysis

| Field | Value |
|---|---|
| **Phase ID** | `PH-01` |
| **Slug** | `phase-01-analysis` |
| **Objective** | Elicit, analyze, validate and baseline requirements; establish the domain model; resolve every `OPEN QUESTION`; identify stakeholders and actors; build the traceability chain. |
| **Status** | `NOT STARTED` — **← NEXT CONTROLLED TASK** |
| **Dependencies** | `PH-00` |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; baselined `docs/01-requirements.md`, `docs/02-use-cases.md`, `docs/03-use-case-actions.md`, `docs/04-flow-actions.md`, `docs/05-flow-events.md`, `docs/06-data-flow.md`, `docs/16-glossary.md`, `docs/17-traceability-matrix.md`; resolved `docs/15-risk-register.md` entries |
| **Exit gate** | `GO` requires: stakeholders identified; requirements are unique, atomic, unambiguous, testable and prioritised; **0 unresolved ambiguities**; traceability matrix complete for every `CONFIRMED` requirement; every `OPEN QUESTION` from Phase 00 resolved or explicitly deferred with an owner; no fabricated requirements; validator green |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 02 — Architecture & Integration Design

| Field | Value |
|---|---|
| **Phase ID** | `PH-02` |
| **Slug** | `phase-02-architecture` |
| **Objective** | Convert every `PROPOSED` architectural hypothesis into accepted ADRs; produce C4 views, data model, API contract, integration design, security design and technology justification. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-01` (must be `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; updated `architecture.md` (delta section); ADRs in `docs/decisions/`; `docs/09-database.md`, `docs/10-api-specification.md`, `docs/11-integration-specification.md`, `docs/12-security-specification.md`, `docs/14-quality-attributes.md`; architecture threat model |
| **Exit gate** | `GO` requires: architecture review passed; threat model created and mitigations defined; technology evaluation matrix completed with conformity checked against `RULES_HINTS.md` §2 (any deviation = user decision); all `PROPOSED` items either `Accepted` via ADR or explicitly rejected; all requirements traceable to design elements; validator green |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 03 — Technical Foundation

| Field | Value |
|---|---|
| **Phase ID** | `PH-03` |
| **Slug** | `phase-03-foundation` |
| **Objective** | Create the toolchain and skeleton that later phases build on: repository structure, CI, lint/test/coverage tooling, migration tooling, secret and dependency scanning, Docker base, auth skeleton. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-02` (must be `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; implemented commands in `RULES_HINTS.md` §3; `permissions-<feature>.md`; migration + rollback rehearsal evidence |
| **Exit gate** | `GO` requires: build 0 errors; lint clean; test harness green; coverage measuring ≥ 80%; secret scan and dependency scan runnable and clean; migration rollback rehearsed; `RULES_HINTS.md` §3 updated in the same commit; **this is the first phase where G1–G7 become executable** |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 04 — Core Traffic Domain

| Field | Value |
|---|---|
| **Phase ID** | `PH-04` |
| **Slug** | `phase-04-core-traffic` |
| **Objective** | Implement the core traffic domain and its supporting domains end-to-end: drivers, vehicles, licenses, violations, fines, penalty points, accidents, incidents, monitoring, signals, reporting and notifications. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-03` (must be `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; full CORE-03 artifact set (use cases, DFD, state machines, sequence/activity diagrams, test plan, permissions matrix, QA file, security audit); state machines for every lifecycle-bearing entity |
| **Exit gate** | `GO` requires: all DOD gates G1–G9 green; 0 dead elements; 0 open `CRITICAL`/`HIGH` findings; every function has happy-path + validation + authorization tests; permissions enforced server-side with tests |
| **Completion state** | `NOT STARTED` — 0% |

> This is where feature/domain work lives. Feature-based "phases" are **not** used here.

---

## PHASE 05 — External System Integration

| Field | Value |
|---|---|
| **Phase ID** | `PH-05` |
| **Slug** | `phase-05-integration` |
| **Objective** | Demonstrate both integration styles: synchronous REST contracts and asynchronous domain events over the broker, through adapters for whichever external systems were confirmed in Phase 01. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-04` (must be `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; adapter implementations; contract tests; dead-letter handling evidence; integration security audit |
| **Exit gate** | `GO` requires: contract tests green for every confirmed boundary; event consumers idempotent and dead-lettered; failure paths tested; **no adapter built for an unconfirmed boundary** (`SYS-04`); 0 open `CRITICAL`/`HIGH` findings |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 06 — UI / Dashboard / Reporting

| Field | Value |
|---|---|
| **Phase ID** | `PH-06` |
| **Slug** | `phase-06-reporting-ui` |
| **Objective** | Build the user-facing application: HCI-conformant UI, dashboards and reporting — every control wired to a real backend handler. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-04` (must be `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; `docs/07-website-structure.md`, `docs/08-ui-ux-specification.md` baselined; `uiux-<phase>.md`; reusable confirmation modal; component inventory test |
| **Exit gate** | `GO` requires: 0 dead buttons/links/routes (automated scan); WCAG 2.1 AA with axe/Lighthouse = 0 serious violations; no `alert()`/`confirm()`/`prompt()`; no hardcoded user-facing strings; responsive across supported breakpoints; G1–G9 green |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 07 — Testing / Security / Performance

| Field | Value |
|---|---|
| **Phase ID** | `PH-07` |
| **Slug** | `phase-07-quality-security` |
| **Objective** | Execute the full quality programme: all test levels, security audit, performance benchmarking, accessibility audit, and remediation of every finding. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-03`, `PH-04`, `PH-05`, `PH-06` (all `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; executed `docs/13-testing-strategy.md`; performance results; security audit with 0 open `CRITICAL`/`HIGH`; QA attribute file with measured results |
| **Exit gate** | `GO` requires: 100% tests pass, 0 silent skips; coverage ≥ 80% overall / 100% critical paths; 0 `CRITICAL`/`HIGH` security findings; 0 secrets in repo; performance budgets met with numbers attached; accessibility audit passed |
| **Completion state** | `NOT STARTED` — 0% |

---

## PHASE 08 — Final Integration / Documentation / Delivery

| Field | Value |
|---|---|
| **Phase ID** | `PH-08` |
| **Slug** | `phase-08-final-delivery` |
| **Objective** | Final integration, complete documentation consistency pass, delivery package, lessons learned, and formal sign-off. |
| **Status** | `NOT STARTED` |
| **Dependencies** | `PH-00` … `PH-07` (all `PASSED`) |
| **Required artifacts** | `TODO.md`, `PLAN.md`, `AUDIT.md`, `_index.md`; full-documentation exact-up-to-date check (AUD-06); delivery package; lessons-learned register; final traceability matrix |
| **Exit gate** | `GO` requires: every document consistent with the implementation; validator green; every `CONFIRMED` requirement traceable end-to-end through the full chain; zero open `CRITICAL`/`HIGH` findings project-wide; sign-off obtained |
| **Completion state** | `NOT STARTED` — 0% |

---

## Summary table

| Phase | Name | Status | Depends on | Completion |
|---|---|---|---|---|
| **00** | Initialization & Governance | **`PASSED`** (`GO`, 41/41 — reconciled 2026-09-26) | — | **100%** — 3 `HIGH` deferred by phase design (`F-005`→01, `F-006`→01/02, `F-012`→03), still open & tracked |
| **01** | Requirements & Domain Analysis | `NOT STARTED` ← **next** | 00 | 0% |
| **02** | Architecture & Integration Design | `NOT STARTED` | 01 | 0% |
| **03** | Technical Foundation | `NOT STARTED` | 02 | 0% |
| **04** | Core Traffic Domain | `NOT STARTED` | 03 | 0% |
| **05** | External System Integration | `NOT STARTED` | 04 | 0% |
| **06** | UI / Dashboard / Reporting | `NOT STARTED` | 04 | 0% |
| **07** | Testing / Security / Performance | `NOT STARTED` | 03, 04, 05, 06 | 0% |
| **08** | Final Integration / Documentation / Delivery | `NOT STARTED` | 00–07 | 0% |

---

## Related documents

- [`all_in_one_track.md`](all_in_one_track.md) — high-level timeline with milestone links
- [`docs/phases/README.md`](docs/phases/README.md) — phase index (links every phase `_index.md`)
- [`Audit.md`](Audit.md) — findings register & remediation waves
- [`ENTRY.md`](ENTRY.md) — orientation & next task
- [`session_track.md`](session_track.md) — resume index
