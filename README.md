# Traffic and Transport Management System (TTMS)

> **Status: PHASE 00 — Initialization & Governance (ACTIVE). No application code exists yet.**

An academically rigorous **Traffic and Transport Management System**, built as a
Fourth-Year Information Technology project for the course
**Systems Integration and Architecture**.

**Repository:** https://github.com/AbdullahMaresh9/Traffic-and-Transport-Management-System.git
· **Branch:** `main` · **Rules:** ADMR v2.0.0 (`senior-rules/`)

---

## Purpose

The objective is to *demonstrate engineering discipline*, not merely to ship a working app.
The project is expected to show:

| | |
|---|---|
| Software Architecture | Systems Integration |
| Domain Modeling | Requirements Engineering |
| API Design | Event-Driven Communication |
| External-System Adapters | Database Architecture |
| Security Architecture | Testing & Quality Assurance |
| Structured SDLC | Traceability & Auditability |
| | AI-assisted engineering governance |

**Working principle:** correctness, architectural clarity, traceability, verifiability and
demonstrable integration concepts are favored over unnecessary production-infrastructure
complexity. This is coursework, not a production service.

## Academic context

| Field | Value |
|---|---|
| Level | Fourth-Year Information Technology |
| Course | Systems Integration and Architecture |
| Nature | Academic engineering project |
| Stakeholders | `OPEN QUESTION` — none identified yet (see `Audit.md` `F-006`) |

## System scope

**Proposed** domain map — see [`mindmap.md`](mindmap.md) for status labels on every node.

- **Core domain:** Traffic Management
- **Supporting domains:** Driver, Vehicle, License, Violation, Accident, Traffic Monitoring,
  Traffic Signals, Reporting, Notifications, Identity & Access, Audit
- **Candidate external systems:** Civil Registry · Police/Emergency · Payment Gateway ·
  Notification Provider · GIS/Mapping · Traffic Sensor/Signal Simulator

**Important:** every item above is a `PROPOSED DOMAIN` / `PROPOSED INTEGRATION BOUNDARY`.
**Zero business requirements have been confirmed.** No violation catalogue, fine tariff,
penalty-point threshold, license class, RBAC role or regulatory obligation is known — and
none has been invented.

### Hard scope fence

`RULES_HINTS.md` **SYS-01** — no application business functionality (no entity CRUD, no
business APIs, no business database models, no business services, no production source
code) may be created before **Phase 01 and Phase 02 exit gates have both explicitly passed.**

## Architectural direction

> **Everything below is `PROPOSED`. It is not final and has not been approved.**
> Each choice becomes a decision only through an ADR in [`docs/decisions/`](docs/decisions/),
> validated during **Phase 02**.

- **Style:** Modular Monolith + Integration Layer + Event-Driven Communication
- **Frontend:** React + TypeScript
- **Backend:** NestJS + TypeScript
- **Database:** PostgreSQL
- **API:** REST + OpenAPI
- **Messaging:** RabbitMQ
- **Authentication:** JWT + RBAC
- **Containerization:** Docker / Docker Compose

The system is intended to demonstrate **both** integration styles — synchronous REST
request/response contracts and asynchronous domain events over a broker. Current model:
[`architecture.md`](architecture.md).

## Documentation structure

Governance is **root-level**; analytical and design detail lives under `docs/`.

```
project/
├── AGENTS.md                      ← operational entry point for AI sessions
├── ENTRY.md                       ← master entry: status, phases, blockers, next task
├── README.md                      ← this file
├── RULES_HINTS.md                 ← rules bound to this project's real commands/paths
├── architecture.md                ← architectural model (all PROPOSED)
├── mindmap.md                     ← conceptual hierarchy with status labels
├── memory.md                      ← cumulative project memory
├── Audit.md                       ← findings register + remediation waves
├── development_phases_entry.md    ← official phase registry (Phase 00–08)
├── all_in_one_track.md            ← high-level timeline
├── session_track.md               ← session resume index
├── CHANGELOG.md                   ← governance changes
│
├── senior-rules/                  ← vendored ADMR v2.0.0 (unmodified core rules)
│   ├── ENTRY.md  RULES.md  VERSION  core/  templates/  adapters/  validators/
│
├── .opencode/
│   ├── agents/                    ← architect, requirements-analyst, backend, frontend,
│   │                                integration, qa-security
│   └── skills/                    ← master-entry, project-analysis, architecture,
│                                    parallel-execution, senior-rules, traffic-domain
│
└── docs/
    ├── 00-project-charter.md … 16-glossary.md   (17 numbered documents)
    ├── 17-traceability-matrix.md
    ├── decisions/                 ← ADRs (none accepted yet)
    ├── phases/                    ← phase-00 … phase-08, each with TODO/PLAN/AUDIT/_index
    └── sessions/                  ← session evidence & raw command output
```

**Document quality rule:** every document carries *Purpose, Scope, Current Status, Known
Context, Confirmed Information, Assumptions, Open Questions, Traceability References,*
and *Related Documents* — with claims labelled `CONFIRMED` / `ASSUMPTION` / `PROPOSED` /
`OPEN QUESTION` / `BLOCKED`. No meaningless placeholders; no invented requirements.

## Development methodology

**Operating principle:** `PLAN → ANALYZE → DOCUMENT → VALIDATE → IMPLEMENT → TEST → AUDIT → SYNCHRONIZE`

**Phases** (see [`development_phases_entry.md`](development_phases_entry.md) — these are
SDLC phases, *not* feature buckets):

| # | Phase | # | Phase |
|---|---|---|---|
| 00 | Initialization & Governance | 05 | External System Integration |
| 01 | Requirements & Domain Analysis | 06 | UI / Dashboard / Reporting |
| 02 | Architecture & Integration Design | 07 | Testing / Security / Performance |
| 03 | Technical Foundation | 08 | Final Integration / Docs / Delivery |
| 04 | Core Traffic Domain | | |

**Authority hierarchy** (conflicts resolve upward — `ENTRY.md` §9):

1. **Senior Implementation Rules** (`senior-rules/`) → mandatory governance & verification
2. **Delegate Skills** → orchestration, parallel execution, phase transitions
3. **Senior Full-Stack Skills** → engineering knowledge & SDLC/testing/security/requirements

**Precedence inside the rules** (`GEN-07`): `SEC` > `DOD` > `GEN-03` (never fake
completion) > `IMP` > `DOC`/`AUD` > all else.

**Status vocabulary:** `DONE` · `INCOMPLETE` (name the failing gate) · `BLOCKED` (reason +
evidence) · `READY-FOR-REVIEW`. Never "should be working".

## Current phase

| Phase | Status |
|---|---|
| **00 — Initialization & Governance** | **`PASSED`**, exit gate **`GO` (41/41)** |
| 01 — Requirements & Domain Analysis | `NOT STARTED` — **next controlled task** (await user instruction) |
| 02–08 | `NOT STARTED` |

Known blockers: **none for Phase 00** (`BLK-01` closed 2026-09-26 — appendix restored
verbatim). Deferred, still open: `F-005` → Phase 01, `F-006` → Phase 01/02,
`F-012` → Phase 03 (`Audit.md` §3.1).

## How to resume the project

1. Read [`AGENTS.md`](AGENTS.md) — the startup protocol.
2. Read [`ENTRY.md`](ENTRY.md) — what the project is, what's active, what's blocked.
3. Read [`session_track.md`](session_track.md) — the latest row and its session file.
4. Read [`development_phases_entry.md`](development_phases_entry.md) — active phase + gate.
5. Read the active phase's `TODO.md` under `docs/phases/phase-NN-*/`.
6. Run the validator and report its output **before** starting work:
   ```
   python senior-rules/validators/validate.py .
   ```
   *(This environment has `python` 3.14.4; `python3` is not available.)*

Paste-ready resume prompt: [`session_track.md`](session_track.md).

## Project governance

- **Mandatory rules:** [`senior-rules/RULES.md`](senior-rules/RULES.md) — 77 rules with
  stable IDs and severities `CRITICAL`/`HIGH`/`MEDIUM`/`LOW`, each with a mechanical
  verification method.
- **Project binding:** [`RULES_HINTS.md`](RULES_HINTS.md) — real commands, paths, conventions
  and project rules `SYS-01`…`SYS-08`.
- **Definition of Done:** nine numeric gates G1–G9
  (`senior-rules/core/01_definition_of_done.md`). Gates that cannot run yet are reported as
  `NOT APPLICABLE`, never as `PASS`.
- **Findings & audits:** [`Audit.md`](Audit.md).
- **Traceability:** [`docs/17-traceability-matrix.md`](docs/17-traceability-matrix.md).
- **Never** claim completion without pasted raw command output (`GEN-04`), and never
  fabricate requirements or stakeholders (`GEN-03`, `SYS-03`).
