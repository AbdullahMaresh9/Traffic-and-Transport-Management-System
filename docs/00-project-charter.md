# 00 — Project Charter

| Field | Value |
|---|---|
| **Purpose** | Establish the project's identity, objectives, scope boundaries and governance at a level high enough to orient any stakeholder or session. |
| **Scope** | Project-level only. No technical or functional detail belongs here. |
| **Current Status** | `CONFIRMED` for identity/objectives (supplied by the project brief). `PROPOSED`/`OPEN QUESTION` for everything stakeholder- or constraint-related. |
| **Phase** | 00 — Initialization & Governance |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

To develop an academically rigorous **Traffic and Transport Management System** that
demonstrates the full breadth of engineering practice required by the course
*Systems Integration and Architecture*.

## 2. Scope

### 2.1 In scope (`CONFIRMED` — from the project brief)

Software architecture · systems integration · domain modeling · requirements engineering ·
API design · event-driven communication · external-system adapters · database architecture ·
security architecture · testing and quality assurance · structured SDLC · traceability ·
auditability · AI-assisted engineering governance.

### 2.2 Out of scope (`CONFIRMED`)

| Excluded | Why |
|---|---|
| Production infrastructure complexity | The brief explicitly favors correctness and clarity over it |
| Commercialisation / marketing / pricing | Academic project (Source A `03_business_marketing` is therefore not adopted) |
| Real regulatory compliance programmes (SOC 2, ISO 27001, HIPAA, PCI-DSS) | Inapplicable to coursework — recorded as `NOT APPLICABLE` (`Audit.md` `L-09` guidance, `AP-10`) |
| Business implementation during Phase 00 | `RULES_HINTS.md` SYS-01 |

### 2.3 Scope boundaries for Phase 00 (`CONFIRMED`)

Phase 00 produces **only**: repository initialization, project governance, documentation
architecture, AI skills integration, senior rules integration, OpenCode configuration,
phase tracking, session tracking, requirements-analysis foundation, initial architecture
foundation.

## 3. Confirmed information

| ID | Fact |
|---|---|
| `CF-CH-01` | Project name: Traffic and Transport Management System |
| `CF-CH-02` | Repository: https://github.com/AbdullahMaresh9/Traffic-and-Transport-Management-System.git · branch `main` |
| `CF-CH-03` | Academic context: Fourth-Year Information Technology |
| `CF-CH-04` | Course: Systems Integration and Architecture |
| `CF-CH-05` | The repository was empty (0 commits) at initialization |
| `CF-CH-06` | The operating principle favors correctness, architectural clarity, traceability, verifiability and demonstrable integration concepts |

## 4. Assumptions

| ID | Assumption | Validation owner |
|---|---|---|
| `AS-CH-01` | A supervisor exists who can answer open questions and sign off phases | User (`F-006`) |
| `AS-CH-02` | There is a submission deadline that constrains the phase plan | Phase 01 (`OQ-10`) |
| `AS-CH-03` | The project is delivered by one primary developer with AI assistance | User |

## 5. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-CH-01` | Who are the stakeholders, and who signs off requirements and architecture? | 01 |
| `OQ-CH-02` | What is the submission deadline and any grading rubric? | 01 |
| `OQ-CH-03` | Are group members involved, and what is the RACI? | 01 |
| `OQ-CH-04` | Is a demonstration/deployment environment required for delivery? | 01 / 08 |

## 6. Stakeholder register

| Stakeholder | Role | Power/Interest | Status |
|---|---|---|---|
| *(unknown)* | Supervisor / reviewer | High / High | `OPEN QUESTION` — **not identified** |
| *(unknown)* | Developer / author | High / High | `OPEN QUESTION` — name not supplied |
| *(unknown)* | End user (citizen / officer / admin) | Low-Med / High | `OPEN QUESTION` — personas not yet created |

> **No stakeholder name has been supplied or invented.** This gap is tracked as
> `Audit.md` `F-006` (`HIGH`) and blocks the Phase 01 baseline sign-off gate.

## 7. RACI (proposed, unconfirmed)

| Activity | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|
| Requirements baseline | AI + developer | **Supervisor** (`OPEN QUESTION`) | Stakeholders (`OPEN QUESTION`) | — |
| Architecture approval | AI + developer | **Supervisor** (`OPEN QUESTION`) | — | — |
| Implementation | AI + developer | Developer | — | — |
| Phase gate decision | AI (evidence assembly) | **Supervisor** (`OPEN QUESTION`) | — | — |

## 8. Traceability references

Upstream: none (this is the root document).
Downstream: [`01-requirements.md`](01-requirements.md) ·
[`17-traceability-matrix.md`](17-traceability-matrix.md) ·
[`../development_phases_entry.md`](../development_phases_entry.md)

## 9. Related documents

- [`../ENTRY.md`](../ENTRY.md) — master entry & active phase
- [`../README.md`](../README.md) — project overview
- [`../mindmap.md`](../mindmap.md) — domain concept hierarchy
- [`../architecture.md`](../architecture.md) — architectural hypothesis
- [`15-risk-register.md`](15-risk-register.md) — risks to this charter
