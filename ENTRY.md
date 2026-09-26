# ENTRY — Master Entry File (read this first)

**Project:** Traffic and Transport Management System (TTMS)
**Repository:** https://github.com/AbdullahMaresh9/Traffic-and-Transport-Management-System.git
**Branch:** `main` · **Rules version:** `2.0.0` (`senior-rules/VERSION`)
**Document status:** `CONFIRMED` for identity and structure; all technical choices remain `PROPOSED`.

---

## 1. What is this project?

An academically rigorous **Traffic and Transport Management System** built as a
Fourth-Year Information Technology project for the course
**Systems Integration and Architecture**.

Its purpose is to *demonstrate engineering discipline*, not merely to ship a working app:

- software architecture and architecture decision records
- systems integration (synchronous **and** asynchronous)
- domain modelling and requirements engineering
- API design (REST + OpenAPI) and event-driven communication
- external-system adapters
- database architecture and security architecture
- testing, quality assurance and traceability
- a structured SDLC with auditability
- AI-assisted engineering governance

> Favor **correctness, architectural clarity, traceability and verifiability** over
> unnecessary production-infrastructure complexity. This is coursework, not a startup.

## 2. Why does it exist?

`CONFIRMED` — The project exists to satisfy the course objective above. No commercial,
regulatory or operational driver has been stated by any stakeholder. Any statement beyond
this is an `ASSUMPTION` or an `OPEN QUESTION` and must be labelled as such.

## 3. What phase is active?

**PHASE 00 — INITIALIZATION & GOVERNANCE: `PASSED` (exit gate `GO`, 41/41).
PHASE 01 — REQUIREMENTS & DOMAIN ANALYSIS: `NOT STARTED` — the next controlled task,
awaiting explicit user instruction. No phase is currently `ACTIVE`.**

| Phase | Name | Status |
|---|---|---|
| 00 | Initialization & Governance | **PASSED** (`GO`, 41/41 — reconciled 2026-09-26) |
| 01 | Requirements & Domain Analysis | NOT STARTED — **next controlled task** |
| 02 | Architecture & Integration Design | NOT STARTED (blocked by 01) |
| 03 | Technical Foundation | NOT STARTED (blocked by 02) |
| 04 | Core Traffic Domain | NOT STARTED (blocked by 03) |
| 05 | External System Integration | NOT STARTED (blocked by 04) |
| 06 | UI / Dashboard / Reporting | NOT STARTED (blocked by 04) |
| 07 | Testing / Security / Performance | NOT STARTED (blocked by 03–06) |
| 08 | Final Integration / Documentation / Delivery | NOT STARTED (blocked by all) |

Authoritative registry: [`development_phases_entry.md`](development_phases_entry.md).

**Hard scope fence (SYS-01):** no application business functionality may be created until
Phase 01 **and** Phase 02 exit gates have both explicitly passed. This is a `CRITICAL`
governance constraint, not a suggestion.

## 4. What has been completed?

Phase 00 work completed so far — with evidence in
[`docs/phases/phase-00-initialization/AUDIT.md`](docs/phases/phase-00-initialization/AUDIT.md):

- [x] Working directory inspected (`pwd`, `git status`, `git remote -v`, `git branch`, tree)
- [x] Correct project repository identified and cloned (it was **empty** — 0 commits)
- [x] Three external knowledge sources cloned to a temporary analysis directory and analyzed
      (inventory, dependency map, skill classification, relevance, rule extraction, conflicts)
- [x] Senior Implementation Rules (ADMR v2.0.0) vendored intact into `senior-rules/`
- [x] `RULES_HINTS.md` adapter created and bound to this actual project
- [x] OpenCode structure initialized: `.opencode/agents/`, `.opencode/skills/`
- [x] Root governance set created: `AGENTS.md`, `ENTRY.md`, `README.md`, `RULES_HINTS.md`,
      `architecture.md`, `mindmap.md`, `memory.md`, `Audit.md`,
      `development_phases_entry.md`, `all_in_one_track.md`, `session_track.md`, `CHANGELOG.md`
- [x] `docs/` architecture created (17 numbered documents + `decisions/`, `phases/`, `sessions/`)
- [x] Phase registry created; all 9 phase directories created with `TODO.md`, `PLAN.md`, `AUDIT.md`
- [x] Requirements- and architecture-analysis foundations initialized (no invented detail)
- [x] Traceability structure initialized
- [x] Validator executed; output recorded

## 5. What remains?

Everything after governance. Concretely:

- **`CLOSED` (2026-09-26):** the `## Permanent Project Management Methodology` section of
  `memory.md` now contains the complete **APPENDIX: PROJECT WHITEBOARD METHODOLOGY**
  verbatim — restored from the preserved copy of the same initialization command and
  corroborated by signature-phrase checks; provenance recorded in `memory.md`.
  See §6 and [`Audit.md`](Audit.md) `F-004`.
- Phase 01 (Requirements & Domain Analysis) — **not started, not to be started this session**
- Phase 02 (Architecture & Integration Design) — not started
- All implementation phases 03–08 — not started

## 6. What is blocked?

| ID | Blocked item | Exact reason | What unblocks it |
|---|---|---|---|
| `BLK-01` | ~~`memory.md` → verbatim appendix~~ | ~~Text not present in the executed instruction context; 0 `WHITEBOARD` matches in the 3 source repos.~~ **Closed 2026-09-26:** full appendix restored verbatim into `memory.md` from the preserved copy of the same initialization command; provenance + 9/10 signature-phrase corroboration recorded there. | **Already unblocked** — verify by reading `memory.md` §*Permanent Project Management Methodology*. |

**No blockers remain for Phase 00** (status `PASSED`). Deferred, still open and tracked
(`Audit.md` §3.1): `F-005` → Phase 01 · `F-006` → Phase 01/02 · `F-012` → Phase 03.

## 7. What architecture is proposed?

**PROPOSED — not approved, not validated.** Full model in
[`architecture.md`](architecture.md).

- **Style:** Modular Monolith + Integration Layer + Event-Driven Communication
- **Frontend:** React + TypeScript
- **Backend:** NestJS + TypeScript
- **Database:** PostgreSQL
- **API:** REST + OpenAPI
- **Messaging:** RabbitMQ
- **Authentication:** JWT + RBAC
- **Containerization:** Docker / Docker Compose

Every line above is `PROPOSED` until validated during **Phase 02** and recorded as ADRs in
[`docs/decisions/`](docs/decisions/). Do not present any of it as final.

## 8. Where are the documents?

| Purpose | Path |
|---|---|
| Operational AI entry point | [`AGENTS.md`](AGENTS.md) |
| Project overview | [`README.md`](README.md) |
| Rules adapter (this project's commands/paths) | [`RULES_HINTS.md`](RULES_HINTS.md) |
| Architecture | [`architecture.md`](architecture.md) |
| Domain concept hierarchy | [`mindmap.md`](mindmap.md) |
| Cumulative project memory | [`memory.md`](memory.md) |
| Findings / audit register | [`Audit.md`](Audit.md) |
| Phase registry & exit gates | [`development_phases_entry.md`](development_phases_entry.md) |
| Full project timeline | [`all_in_one_track.md`](all_in_one_track.md) |
| Session resume index | [`session_track.md`](session_track.md) |
| Governance change log | [`CHANGELOG.md`](CHANGELOG.md) |
| Requirements foundation | [`docs/01-requirements.md`](docs/01-requirements.md) |
| Traceability matrix | [`docs/17-traceability-matrix.md`](docs/17-traceability-matrix.md) |
| All analysis & design docs | [`docs/`](docs/) |
| Per-phase artifacts | [`docs/phases/`](docs/phases/) |
| Session evidence | [`docs/sessions/`](docs/sessions/) |
| Architecture decision records | [`docs/decisions/`](docs/decisions/) |

## 9. What are the mandatory rules?

- **Catalog:** [`senior-rules/RULES.md`](senior-rules/RULES.md) — 77 rules, stable IDs,
  severities `CRITICAL`/`HIGH`/`MEDIUM`/`LOW`, each with a mechanical verification method.
- **Meta-rules:** [`senior-rules/core/00_meta_rules.md`](senior-rules/core/00_meta_rules.md)
  — severity semantics, precedence, amendment procedure, the five-role review.
- **Definition of Done:** [`senior-rules/core/01_definition_of_done.md`](senior-rules/core/01_definition_of_done.md)
  — nine numeric gates G1–G9.
- **Project binding:** [`RULES_HINTS.md`](RULES_HINTS.md) — real commands, real paths, and
  the project-specific rules `SYS-01`…`SYS-08`.
- **Precedence (GEN-07):** `SEC` > `DOD` > `GEN-03` (never fake completion) > `IMP` >
  `DOC`/`AUD` > all else.

**Authority hierarchy across the three integrated sources:**

1. **Senior Implementation Rules** → mandatory governance / verification *(highest)*
2. **Delegate Skills** → orchestration / parallel execution / phase transitions
3. **Senior Full-Stack Skills** → engineering knowledge / architecture / SDLC / testing /
   security / requirements / integration / UI-UX *(lowest)*

Never weaken a `CRITICAL` rule; never modify a core rule to make validation pass; if
evidence is unavailable, the status is `BLOCKED`.

## 10. What should the next session do?

**NEXT CONTROLLED TASK: PHASE 01 — REQUIREMENTS & DOMAIN ANALYSIS.**
Do **not** begin it automatically in the Phase 00 session.

Resume prompt (paste-ready, per `senior-rules/core/02_sessions_and_recovery.md`):

```
RESUME PROMPT — paste into new session:
Read ENTRY.md, RULES.md, RULES_HINTS.md, session_track.md, and development_phases_entry.md.
Continue from session 003 (docs/sessions/session-003.md); 001 = Phase 00 bootstrap,
002 = reconciliation, 003 = consistency cleanup.
Next task: PHASE 01 — Requirements & Domain Analysis (docs/phases/phase-01-analysis/TODO.md)
  — requires explicit user instruction; do not start automatically.
Last completed: PHASE 00 — Initialization & Governance, status PASSED (GO, 41/41) after
  the 2026-09-26 reconciliation; BLK-01 closed (appendix restored verbatim in memory.md).
Deferred, still open: F-005 -> Phase 01 (external systems), F-006 -> Phase 01/02
  (stakeholder/sign-off), F-012 -> Phase 03 (CI/scanners). None blocks Phase 00.
Run: python senior-rules/validators/validate.py .   and report its output before starting.
Scope fence: RULES_HINTS.md SYS-01 — no business implementation until Phase 01 AND
  Phase 02 exit gates have both PASSED (SYS-08). Do not push without asking.
```

**Session discipline:** follow the startup protocol in [`AGENTS.md`](AGENTS.md). The
repository — not chat history — is the durable source of truth.
