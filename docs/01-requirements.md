# 01 — Requirements Analysis Foundation

| Field | Value |
|---|---|
| **Purpose** | Establish what is currently known about the project's requirements — and, just as importantly, what is *not* known — without inventing anything. |
| **Scope** | Category-level foundation only. Detailed, baselined requirements belong to **Phase 01**. |
| **Current Status** | `CONFIRMED` problem context and purpose; **0 confirmed business requirements**; everything functional is `PROPOSED`/`OPEN QUESTION`. |
| **Phase** | 00 — Initialization & Governance (foundation) → baselined in Phase 01 |
| **Last updated** | 2026-09-26 |
| **Baseline** | **Not baselined.** No requirement may be treated as approved until the Phase 01 exit gate passes. |

> **Anti-fabrication rule in force:** a requirement that cannot be traced to a stakeholder
> statement or to the project brief is **not** a requirement. Where information is missing,
> this document records an `OPEN QUESTION` rather than a plausible-sounding requirement
> (`SYS-03`, `GEN-03`).

---

## 1. Problem Context

### 1.1 What is known (`CONFIRMED`)

The course requires the development of a **Traffic and Transport Management System** that
demonstrates architecture, integration, domain modeling, requirements engineering, API
design, event-driven communication, external-system adapters, database and security
architecture, testing/QA, a structured SDLC, traceability, auditability and AI-assisted
engineering governance.

### 1.2 What is explicitly unknown

| Unknown | Impact |
|---|---|
| Who experiences the problem, and what is the problem exactly? | No problem statement can be validated → `OQ-R-01` |
| Whether any real-world agency, regulation or process is involved | No compliance or process requirements can be asserted |
| Whether the "system" is a real operational need or a demonstration vehicle | Affects realism, data and NFR targets |
| The volume, geography and ownership of traffic data | Blocks NFR baselining |

> This document does **not** assert a problem statement, because none was supplied.
> Writing one would be fabrication.

## 2. Project Purpose

| Field | Value |
|---|---|
| Purpose | Develop an academically rigorous Traffic and Transport Management System demonstrating the course's engineering objectives (see [`00-project-charter.md`](00-project-charter.md) §1) |
| Status | `CONFIRMED` |
| Source | Project brief |

## 3. Stakeholders

| Stakeholder | Role | Status |
|---|---|---|
| Course supervisor / reviewer | Approves requirements, architecture, phase gates | `OPEN QUESTION` — **not identified** |
| Developer / author | Builds the system | `OPEN QUESTION` — name not supplied |
| End users (see §4) | Use the system | `OPEN QUESTION` — no personas created |
| External system owners (see §8) | Provide integration contracts | `OPEN QUESTION` |

**No stakeholder has been named, contacted or quoted.** Tracked as `Audit.md` `F-006`.

## 4. Candidate Actors

All rows are `OPEN QUESTION` unless noted. **None has been confirmed by a stakeholder.**

| ID | Candidate actor | Intent (hypothesised) | Status |
|---|---|---|---|
| `ACT-01` | Citizen | View own records/notifications, pay fines | `OPEN QUESTION` |
| `ACT-02` | Driver | Hold a license, accrue penalty points, receive violations | `OPEN QUESTION` |
| `ACT-03` | Traffic officer | Record/report violations and accidents | `OPEN QUESTION` |
| `ACT-04` | Traffic controller / operator | Monitor congestion and signals | `OPEN QUESTION` |
| `ACT-05` | Reporting analyst | Produce and consume reports | `OPEN QUESTION` |
| `ACT-06` | System administrator | Manage users, roles, permissions, configuration | `PROPOSED` — required by `senior-rules` templates |
| `ACT-07` | Auditor | Read the audit trail | `PROPOSED` — required by the audit concept |
| `ACT-08` | External system (machine actor) | Exchange requests/events with TTMS | `PROPOSED` — see §8 |

> **Actors are not requirements.** Adding an actor implies workflows, permissions and data
> that are all unknown. Resolve in Phase 01.

## 5. Candidate Users

| Field | Value |
|---|---|
| Count | `OPEN QUESTION` — unknown |
| Personas | **None created.** Creating them now would fabricate user research. |
| Demographics / devices / cultures / abilities | `OPEN QUESTION` (Source A `13_hci_uiux` supplies the *method*, not the data) |
| Access channels | `OPEN QUESTION` — web assumed only as an `ASSUMPTION` |

## 6. Functional Requirement Categories

Category-level inventory derived from [`../mindmap.md`](../mindmap.md). **Every row is
`PROPOSED`.** Individual functional requirements, acceptance criteria and use cases are
produced in Phase 01.

| ID | Category | Domain | Status | Notes |
|---|---|---|---|---|
| `FR-CAT-01` | Traffic incident management | Traffic Management | `PROPOSED` | Relationship to "accident" unresolved (`OQ-05`) |
| `FR-CAT-02` | Traffic monitoring & congestion observation | Traffic Monitoring | `PROPOSED` | Measurement source unknown |
| `FR-CAT-03` | Traffic signal monitoring | Traffic Signals | `PROPOSED` | Control vs. monitor unresolved (`MQ-02`) |
| `FR-CAT-04` | Driver management | Driver Management | `PROPOSED` | |
| `FR-CAT-05` | Vehicle management | Vehicle Management | `PROPOSED` | |
| `FR-CAT-06` | Driving license management | License Management | `PROPOSED` | Issuing authority unknown (`OQ-04`) |
| `FR-CAT-07` | Violation management | Violation Management | `PROPOSED` | **Catalogue unknown — must not be invented** |
| `FR-CAT-08` | Fine calculation & payment | Violation / Payment | `PROPOSED` | Tariff unknown; gateway boundary unconfirmed |
| `FR-CAT-09` | Penalty point management | License / Violation | `PROPOSED` | Thresholds unknown |
| `FR-CAT-10` | Accident management | Accident Management | `PROPOSED` | |
| `FR-CAT-11` | Reporting & dashboards | Reporting | `PROPOSED` | Scope unknown (`OQ-11`) |
| `FR-CAT-12` | Notification delivery | Notifications | `PROPOSED` | Channels unknown |
| `FR-CAT-13` | Identity, authentication & authorization | Identity & Access | `PROPOSED` | Roles unknown (`OQ-06`) |
| `FR-CAT-14` | Audit trail & activity logging | Audit | `PROPOSED` | Schema doctrine exists in `senior-rules/core/07` |
| `FR-CAT-15` | Integration with external systems | Integration | `PROPOSED` | All 6 boundaries unconfirmed (`F-005`) |

**Explicitly NOT implied:** that all 15 categories will be implemented, or that any specific
behaviour within them has been agreed.

## 7. Non-Functional Requirement Categories

No numeric target has been confirmed by a stakeholder. The categories below are the ones
that **must** be quantified in Phase 01/02. Targets are deliberately left blank.

| ID | Category | What must be measured | Target | Status |
|---|---|---|---|---|
| `NFR-CAT-01` | Performance | p95 read/write latency, page interactive time, TTFB, bundle size | `OPEN QUESTION` | Rule defaults exist in `RULES_HINTS.md` §6 but are **not confirmed as this project's** |
| `NFR-CAT-02` | Reliability / availability | uptime, failure rate, recovery objectives | `OPEN QUESTION` | |
| `NFR-CAT-03` | Scalability | concurrent users, data volume, growth | `OPEN QUESTION` | |
| `NFR-CAT-04` | Security | auth model, data classes, encryption, retention | `OPEN QUESTION` | Doctrine in `12-security-specification.md` |
| `NFR-CAT-05` | Usability | task effort, error rates, SUS | `OPEN QUESTION` | |
| `NFR-CAT-06` | Accessibility | conformance level | **WCAG 2.1 AA** | `PROPOSED` (rule UI-02 default) |
| `NFR-CAT-07` | Maintainability | modularity, test coverage | ≥ 80% / 100% critical | `PROPOSED` (rule DOD-04 default) |
| `NFR-CAT-08` | Portability / deployability | environments, container targets | `OPEN QUESTION` | |
| `NFR-CAT-09` | Internationalization | locales, RTL | `OPEN QUESTION` (`OQ-08`) | |
| `NFR-CAT-10` | Auditability | what must be reconstructible from logs | `PROPOSED` per `core/07` | |

## 8. Constraints

| ID | Constraint | Type | Status |
|---|---|---|---|
| `CON-01` | Phase 00 forbids business implementation until Phases 01 and 02 both pass | Process | `CONFIRMED` (`SYS-01`) |
| `CON-02` | Academic context: favor clarity/verifiability over production complexity | Context | `CONFIRMED` |
| `CON-03` | Root-level governance files are canonical | Structure | `CONFIRMED` |
| `CON-04` | Core ADMR rules must not be modified | Rule | `CONFIRMED` (`ADP-03`) |
| `CON-05` | Proposed stack: React/TS, NestJS/TS, PostgreSQL, REST+OpenAPI, RabbitMQ, JWT+RBAC, Docker | Technical | **`PROPOSED`** — not a constraint until Phase 02 accepts it |
| `CON-06` | No stakeholder named → cannot baseline requirements | Blocking | `BLOCKED` (`F-006`) |
| `CON-07` | Deadline unknown | Schedule | `OPEN QUESTION` (`OQ-10`) |

## 9. Assumptions

| ID | Assumption | Validation owner |
|---|---|---|
| `AS-R-01` | The system is primarily a demonstration vehicle rather than a production deployment | Phase 01 |
| `AS-R-02` | Single locale `en`, no RTL | Phase 01 (`OQ-08`) |
| `AS-R-03` | External systems will be demonstrated via simulators/adapters rather than real integrations | Phase 01/02 (`OQ-02`, `OQ-12`) |
| `AS-R-04` | Web is the primary access channel | Phase 01 |
| `AS-R-05` | The 15 functional categories above are all in *conceptual* scope | Phase 01 (MoSCoW prioritisation) |

## 10. Open Questions

| ID | Question | Severity if unresolved | Target phase |
|---|---|---|---|
| `OQ-R-01` | What is the actual problem, and who experiences it? | `CRITICAL` | 01 |
| `OQ-R-02` | Who are the stakeholders and the sign-off authority? | `CRITICAL` | 01 |
| `OQ-R-03` | Which of the 15 functional categories are `Must have` vs. `Won't have`? | `HIGH` | 01 |
| `OQ-R-04` | What is the violation catalogue, fine tariff, penalty-point threshold and license-class set? | `CRITICAL` | 01 |
| `OQ-R-05` | What are the RBAC roles and permission matrix? | `HIGH` | 01/02 |
| `OQ-R-06` | Which external systems are real and reachable? | `HIGH` | 01/02 |
| `OQ-R-07` | What are the measurable NFR targets? | `HIGH` | 01/02 |
| `OQ-R-08` | Is a "traffic incident" distinct from an "accident"? | `MEDIUM` | 01 |
| `OQ-R-09` | Does the system control signals or only monitor them? | `MEDIUM` | 01 |
| `OQ-R-10` | Who issues driving licenses? | `HIGH` | 01 |
| `OQ-R-11` | Deadline and grading rubric? | `HIGH` | 01 |
| `OQ-R-12` | Which UI/dashboards are in scope, for which actor? | `MEDIUM` | 01/06 |

## 11. Scope boundaries

| | |
|---|---|
| **In scope for this document** | Problem context, purpose, stakeholders, candidate actors/users, functional and non-functional *categories*, constraints, assumptions, open questions |
| **Out of scope for this document** | Individual requirements with IDs and acceptance criteria, user stories, use cases, business rules, prioritisation, traceability rows — all produced in **Phase 01** |
| **Never in scope** | Invented violation catalogues, tariffs, thresholds, roles, regulations or stakeholder quotes |

## 12. Traceability references

- **Upstream:** [`00-project-charter.md`](00-project-charter.md) → purpose & scope
- **Sideways:** [`../mindmap.md`](../mindmap.md) (concept source) ·
  [`../architecture.md`](../architecture.md) (boundary source)
- **Downstream:** [`02-use-cases.md`](02-use-cases.md) ·
  [`16-glossary.md`](16-glossary.md) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md) ·
  [`15-risk-register.md`](15-risk-register.md)
- **Chain (SYS-05):** Requirement → User Story → Use Case → Business Rule → Domain Component
  → API → Database → Event → Integration → Test Case → Phase

## 13. Related documents

- [`00-project-charter.md`](00-project-charter.md)
- [`02-use-cases.md`](02-use-cases.md)
- [`14-quality-attributes.md`](14-quality-attributes.md)
- [`15-risk-register.md`](15-risk-register.md)
- [`16-glossary.md`](16-glossary.md)
- [`../phases/phase-01-analysis/PLAN.md`](phases/phase-01-analysis/PLAN.md)
