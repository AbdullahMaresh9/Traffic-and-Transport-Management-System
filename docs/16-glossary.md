# 16 — Glossary

| Field | Value |
|---|---|
| **Purpose** | Give every domain and governance term exactly one meaning, so documents cannot diverge in interpretation. |
| **Scope** | Terms actually used in this project's documents. |
| **Current Status** | Governance terms `CONFIRMED`; **domain terms are `PROPOSED` / `OPEN QUESTION`** — a domain term is only confirmed once its concept is. |
| **Phase** | 00 (created) → extended continuously |
| **Last updated** | 2026-09-26 |

---

## A · Governance & status terms (`CONFIRMED`)

| Term | Definition |
|---|---|
| **`CONFIRMED`** | Verified by a stakeholder statement or direct repository evidence. May be relied upon. |
| **`ASSUMPTION`** | An unstated input provisionally held. Never to be presented as a requirement. |
| **`PROPOSED`** | A candidate design/requirement not yet validated or accepted. Requires an ADR (architecture) or Phase 01 baseline (requirements). |
| **`OPEN QUESTION`** | An unresolved item that must be answered by a human, not guessed. |
| **`BLOCKED`** | Cannot progress; an external input is required. Must state the reason and the unblock condition. |
| **`DONE`** | All applicable Definition-of-Done gates green, with pasted evidence. |
| **`INCOMPLETE`** | One or more gates failing; the failing gate must be named. |
| **`READY-FOR-REVIEW`** | Work finished by the agent, awaiting human review. |
| **`NOT APPLICABLE`** | The check cannot apply in the current phase; must give a reason. Never a substitute for `PASS`. |
| **Gate** | A verifiable condition that must hold before a phase may be marked `PASSED`. |
| **Exit gate** | The full set of gates for a phase. |
| **Definition of Done (DoD)** | The nine numeric gates G1–G9 in `senior-rules/core/01_definition_of_done.md`. |
| **Finding** | Something already found wrong; recorded in [`../Audit.md`](../Audit.md) with ID, severity, evidence, owner, status, resolution, date. |
| **Risk** | Something that might go wrong; recorded in [`15-risk-register.md`](15-risk-register.md). |
| **ADR** | Architecture Decision Record: context, decision, consequences, alternatives rejected, compliance. |
| **Severity** | `CRITICAL` / `HIGH` / `MEDIUM` / `LOW` — the canonical taxonomy; all other taxonomies map to it. |
| **Traceability chain** | `Requirement → User Story → Use Case → Business Rule → Domain Component → API → Database → Event → Integration → Test Case → Phase`. |
| **Artifact** | A required document produced by a phase (`core/03` defines the 16-artifact set). |
| **Remediation wave** | A batch of findings grouped by severity and executed until nothing remains (`AUD-03`). |
| **Roll-up** | Phase → phase index → `development_phases_entry.md` → `all_in_one_track.md`; no orphan documents (`DOC-04`). |

## B · Architecture & integration terms (`CONFIRMED` as terms; referents `PROPOSED`)

| Term | Definition |
|---|---|
| **Modular monolith** | A single deployable composed of explicitly bounded modules. The `PROPOSED` architectural style. |
| **Integration layer** | The isolating layer between the system and external systems, implemented as adapters. |
| **Adapter** | A component translating between TTMS's internal model and one external system's contract. |
| **Domain event** | A past-tense record that something happened in a domain (`ViolationRecorded`). |
| **Synchronous integration** | Request/response interaction where the caller waits for the answer (REST). |
| **Asynchronous integration** | Interaction via published events consumed independently (message broker). |
| **Contract** | The published, versioned interface (OpenAPI document or event schema) both sides agree to. |
| **Contract test** | A test proving a producer/consumer still honours the published contract. |
| **Dead-letter queue** | A destination for messages that cannot be processed, preventing loss and blocking. |
| **Idempotency** | The property that processing the same input twice has the same effect as once. |
| **Outbox** | A transactional table that guarantees events are emitted atomically with state changes. |
| **Trust boundary** | A point where data crosses between regions of differing trust (browser↔API, API↔DB, API↔external). |
| **`PROPOSED INTEGRATION BOUNDARY`** | A candidate external system not yet confirmed to exist, be reachable, or be in scope. |
| **C4** | Context / Container / Component / Code structural views. |
| **Bounded context** | A DDD boundary within which a domain model is internally consistent. |

## C · Domain terms (`PROPOSED` / `OPEN QUESTION` — see [`../mindmap.md`](../mindmap.md))

> These are **working definitions, not agreed ones.** Each is flagged with the open question
> that must be resolved before it can be treated as `CONFIRMED`.

| Term | Working definition | Status |
|---|---|---|
| **Traffic Management** | The core domain: monitoring and managing traffic flow, incidents and signals. | `PROPOSED DOMAIN` |
| **Traffic Incident** | A disruptive event on the road network. | `OPEN QUESTION` — vs. Accident (`OQ-05`) |
| **Accident** | A collision event involving vehicles/parties. | `OPEN QUESTION` |
| **Violation** | A recorded breach of a traffic rule. | `PROPOSED` — catalogue unknown (`OQ-R-04`) |
| **Fine** | The monetary consequence of a violation. | `PROPOSED` — tariff unknown |
| **Penalty points** | Points accrued against a license by violations. | `PROPOSED` — thresholds unknown |
| **Driving License** | The authorization held by a driver, with class and validity period. | `PROPOSED` — issuing authority unknown (`OQ-R-10`) |
| **Driver** | A person holding a license. | `OPEN QUESTION` — distinct from Citizen? |
| **Citizen** | A natural person known to the system. | `OPEN QUESTION` |
| **Vehicle** | A registered machine capable of being driven. | `PROPOSED` |
| **Congestion** | Degraded traffic flow; how it is measured is unknown. | `OPEN QUESTION` (`MQ-03`) |
| **Traffic signal** | A control device; this system may monitor or control it. | `OPEN QUESTION` (`MQ-02`) |
| **Road** | A routable way. Owned by TTMS or by GIS? | `OPEN QUESTION` (`MQ-04`) |
| **Notification** | A message delivered to a recipient through a channel. | `PROPOSED` — channels unknown |
| **Report** | A structured aggregation of data for analysis. | `PROPOSED` |
| **Audit trail** | The immutable record of who did what, when, with what result. | `PROPOSED` (`LOG-01`) |

## D · Testing & quality terms (`CONFIRMED` as terms)

| Term | Definition |
|---|---|
| **Test pyramid** | Unit (base) → component → integration → system → E2E (apex), with performance and security suites alongside. |
| **Critical path** | Auth, authz, payments, core CRUD, transactions — requires **100%** coverage. |
| **Dead element** | A button, link, route or DB transaction rendered/exposed but not wired to a real handler. Target: **0**, proven by automated scan. |
| **Regression suite** | Tests that must pass on every change; red = no merge. |
| **Silent skip** | A test that passes by not running. Forbidden without a tracked ticket reference. |
| **Quality attribute scenario** | `Source / Stimulus / Environment / Artifact / Response / Response Measure`. |
| **WCAG 2.1 AA** | The accessibility conformance target (`UI-02`). |

## E · Rules system terms (`CONFIRMED`)

| Term | Definition |
|---|---|
| **ADMR** | AI Development Master Rules — the vendored rule system in `senior-rules/`, version `2.0.0`. |
| **Adapter (`RULES_HINTS.md`)** | The project-specific file binding stack-agnostic rules to real commands and paths (`ADP-01`). |
| **Core rule** | A file under `senior-rules/core/` — never modified by this project (`ADP-03`). |
| **Five-role review** | Senior Engineer · Project Manager · Security Engineer · QA Lead · Architect — all five must be satisfied before claiming a phase complete (`core/00` §0.7). |
| **Precedence** | `SEC` > `DOD` > `GEN-03` > `IMP` > `DOC`/`AUD` > all else (`GEN-07`). |

## Traceability references

- **Upstream:** [`../mindmap.md`](../mindmap.md) (domain concepts) ·
  [`../senior-rules/RULES.md`](../senior-rules/RULES.md) (rule terms) ·
  [`../RULES_HINTS.md`](../RULES_HINTS.md) (project terms)
- **Downstream:** every document in `docs/`; [`17-traceability-matrix.md`](17-traceability-matrix.md)

## Related documents

- [`../mindmap.md`](../mindmap.md)
- [`01-requirements.md`](01-requirements.md)
- [`../Audit.md`](../Audit.md)
- [`../senior-rules/RULES.md`](../senior-rules/RULES.md)
