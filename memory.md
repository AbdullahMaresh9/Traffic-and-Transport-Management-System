# memory.md — Cumulative Project Memory

> This file is the durable, cumulative memory of the project. It is updated whenever a
> **durable** fact changes (a convention adopted, a decision made, a lesson learned) — not
> on every edit. Session-level detail belongs in `docs/sessions/`.
>
> Governing rules: `DOC-01`, `SES-02`, `SES-05`, `core/02_sessions_and_recovery.md`,
> `core/11_communication.md`.

---

# Project Identity

| Field | Value |
|---|---|
| Project name | **Traffic and Transport Management System** (TTMS) |
| Repository | https://github.com/AbdullahMaresh9/Traffic-and-Transport-Management-System.git |
| Default branch | `main` |
| Academic context | Fourth-Year Information Technology |
| Course | Systems Integration and Architecture |
| Project nature | Academic engineering project (coursework, not production/commercial) |
| Governance source | AI Development Master Rules (ADMR) v2.0.0, vendored in `senior-rules/` |

# Project Objectives

`CONFIRMED` — the project objective is to develop an academically rigorous Traffic and
Transport Management System demonstrating:

- Software Architecture
- Systems Integration
- Domain Modeling
- Requirements Engineering
- API Design
- Event-Driven Communication
- External-System Adapters
- Database Architecture
- Security Architecture
- Testing and Quality Assurance
- Structured SDLC
- Traceability
- Auditability
- AI-assisted engineering governance

**Operating principle for all work:** correctness, architectural clarity, traceability,
verifiability and demonstrable integration concepts are preferred over unnecessary
production-infrastructure complexity.

# Current Project State

| Field | Value |
|---|---|
| Active phase | **PHASE 00 — Initialization & Governance** |
| Phase 00 status | See `development_phases_entry.md` (authoritative) |
| Application code | **None.** Zero application source, manifests, containers, databases. |
| Repository state | Initialized; governance baseline committed on `main` |
| Accepted ADRs | **0** — every technical choice remains `PROPOSED` |
| Confirmed business requirements | **0** |
| Session | 001 — see `docs/sessions/session-001.md` |

**In force right now:** `RULES_HINTS.md` SYS-01 / SYS-08 — no application business
functionality until Phase 01 **and** Phase 02 exit gates have both explicitly passed.

# Current Architecture Hypothesis

**Status: `PROPOSED` — not approved, not validated.** Full model in `architecture.md`.

- **Style:** Modular Monolith + Integration Layer + Event-Driven Communication
- **Frontend:** React + TypeScript
- **Backend:** NestJS + TypeScript
- **Database:** PostgreSQL
- **API:** REST + OpenAPI
- **Messaging:** RabbitMQ
- **Authentication:** JWT + RBAC
- **Containerization:** Docker / Docker Compose

**Integration model (both styles to be demonstrated):** synchronous REST request/response
contracts **and** asynchronous domain events over a message broker.

**Domain map:** one core domain (Traffic Management) plus 11 supporting domains and 6
candidate external systems — every one a `PROPOSED DOMAIN` / `PROPOSED INTEGRATION
BOUNDARY`. See `mindmap.md` and `architecture.md` §4.

# Established Conventions

`CONFIRMED` — these are in force from Phase 00 onward.

| Convention | Value |
|---|---|
| Documentation language | English |
| Doc naming | Ordered numeric prefixes `00-` … `16-` under `docs/`; phases `phase-NN-<slug>/`; sessions `session-NNN.md` |
| Governance location | **Root level** (never all under `docs/`); analytical detail under `docs/` |
| Claim labelling | `CONFIRMED` · `ASSUMPTION` · `PROPOSED` · `OPEN QUESTION` · `BLOCKED` |
| Status vocabulary | `DONE` · `INCOMPLETE` (name failing gate) · `BLOCKED` (reason + evidence) · `READY-FOR-REVIEW` |
| Gate decision vocabulary | `GO` · `CONDITIONAL GO` · `NO-GO` |
| Severity vocabulary | `CRITICAL` · `HIGH` · `MEDIUM` · `LOW` (the canonical taxonomy; all others map to it) |
| Branching | Trunk-based off `main`; `feat/`, `fix/`, `chore/`, `docs/`, `security/` prefixes |
| Commits | Conventional Commits `type(scope): subject`; commit only after gates pass |
| Evidence rule | Raw command output pasted into the session file **before** any completion claim (GEN-04) |
| Docs + code | Updated in the **same commit** (DOC-05) |
| Secrets | Never committed; `.env*` gitignored from day zero (SEC-01) |
| Validator invocation | `python senior-rules/validators/validate.py .` (Windows/PowerShell: `python`, not `python3`) |
| Questions | Ask before implementing on ambiguity (COM-01); batch them (COM-02) |
| Reporting | Unprompted **Done / Remaining / Next** after each phase/task (COM-03, AUD-04) |
| Accessibility target | WCAG 2.1 AA (UI-02) |
| Coverage target | ≥ 80% overall, 100% critical paths (DOD-04) |

# Architectural Decisions

**None accepted.** No ADR exists. Registry: `docs/decisions/`.

Every stack and pattern choice listed in *Current Architecture Hypothesis* is `PROPOSED`
and requires an ADR (context / decision / consequences / alternatives rejected /
compliance) before it may be treated as a decision — per `core/10_architecture.md` §10.3
and `RULES_HINTS.md` SYS-06.

# Confirmed Facts

`CONFIRMED` = verified by direct evidence, not inference.

| # | Fact | Evidence |
|---|---|---|
| CF-01 | The target repository existed but was **empty** (0 commits) when cloned; branch `main` had no commits. | `git clone` output: *"warning: You appear to have cloned an empty repository"*; `git log` → *fatal: your current branch 'main' does not have any commits yet* |
| CF-02 | The working directory is `D:\IT-Level-4\IT-Level4-part1\project\Traffic-and-Transport-Management-System` and contained **zero** files before clone. | `pwd`; recursive file count = `0` |
| CF-03 | Environment is Windows + PowerShell; `git 2.45.1`, `python 3.14.4`, `node v24.14.1`, `npm 11.11.0`. `python3` is **not** available. | tool version output |
| CF-04 | Three external knowledge sources were cloned and analyzed: pro-skills (14 skills ×2 copies), delegate-skills (16 skills), senior-implementation-rules (ADMR). | analysis record in `docs/phases/phase-00-initialization/AUDIT.md` |
| CF-05 | ADMR vendored into `senior-rules/` passes its own validator checks for signatures (26 files), rule-ID uniqueness (**77 rules**) and internal links (0 broken). | validator output |
| CF-06 | OpenCode discovers skills at `<root>/skills` (i.e. `.opencode/skills/`) and agents via `{agent,agents}/**/*.md`. | string scan of the installed `opencode.exe` |
| CF-07 | The three source repositories contain **no** `WHITEBOARD` match anywhere. | repo-wide `Select-String "WHITEBOARD"` → 0 results |
| CF-08 | The ADMR source has an internal version discrepancy: `VERSION` = `2.0.0`, `CHANGELOG.md` latest entry = `[2.1.0]`. | direct file read |

# Assumptions

Every row is **unvalidated**. `ASSUMPTION` must never be presented as a requirement.

| # | Assumption | Why we are holding it | Validation owner |
|---|---|---|---|
| AS-01 | The proposed stack (React/NestJS/PostgreSQL/RabbitMQ/JWT+RBAC/Docker) is acceptable for this course. | Stated in the Phase 00 brief as "potential technology direction". | Phase 02 |
| AS-02 | A modular monolith best satisfies the course objective for this project. | Simplifies demonstration of module boundaries + integration. | Phase 02 ADR |
| AS-03 | The listed external systems are *conceptually* in scope for demonstration purposes (likely via simulators). | The brief lists them as proposed integration boundaries. | Phase 01 |
| AS-04 | Single locale `en`, no RTL requirement. | No locale stated anywhere. | Phase 01 / `AQ-06` |
| AS-05 | A human supervisor exists who can answer `OPEN QUESTION`s. | Inherent to an academic project. | User |
| AS-06 | The project will be built by one primary developer plus AI agents. | Small academic scope. | User |

# Open Questions

Unresolved. **Do not answer these by inventing content.** (SYS-03)

| ID | Question | Area | Target phase |
|---|---|---|---|
| `BLK-01` | ~~The verbatim "APPENDIX: PROJECT WHITEBOARD METHODOLOGY" was not supplied. What is its text?~~ | Governance | **`CLOSED` 2026-09-26** — restored verbatim under *Permanent Project Management Methodology*; see the provenance record there |
| `OQ-01` | Who are the stakeholders, and who signs off requirements? | Requirements | 01 |
| `OQ-02` | Are the six candidate external systems real and reachable? | Integration | 01 / 02 |
| `OQ-03` | What is the violation catalogue, fine tariff and penalty-point threshold? *(must not be invented)* | Domain | 01 |
| `OQ-04` | Who issues driving licenses — this system or the Civil Registry? | Domain | 01 |
| `OQ-05` | Is a "Traffic Incident" distinct from an "Accident"? | Domain | 01 |
| `OQ-06` | What are the RBAC roles and their permission matrix? | Security | 01 / 02 |
| `OQ-07` | What are the measurable non-functional targets (concurrency, uptime, p95)? | Quality | 01 / 02 |
| `OQ-08` | Single-locale or multi-locale/RTL? | UI-UX | 01 |
| `OQ-09` | Which diagrams does the supervisor expect, and at what detail? | Process | 01 |
| `OQ-10` | Is there a submission deadline that constrains the phase plan? | Planning | 01 |
| `OQ-11` | Which UI/dashboards are in scope, and for which actor? | UI-UX | 01 / 06 |
| `OQ-12` | Is a simulator acceptable in place of real traffic sensors/signals? | Integration | 01 / 02 |

Full list with owners: `docs/01-requirements.md` §Open Questions, `architecture.md` §8,
`docs/15-risk-register.md`.

# Known Constraints

| # | Constraint | Type |
|---|---|---|
| `C-01` | Phase 00 is a hard scope fence — no business implementation until Phase 01 **and** Phase 02 pass. | Process (`SYS-01`) |
| `C-02` | Academic context: favour clarity/verifiability over production-infrastructure complexity. | Context |
| `C-03` | Core ADMR rule files must never be modified to make validation pass (ADP-03). | Rule |
| `C-04` | Root-level governance files are canonical; do not duplicate them under `docs/`. | Structure |
| `C-05` | `python3` does not exist in this environment; use `python`. | Environment (CF-03) |
| `C-06` | No dependency manifest, lockfile, CI, or secret scanner exists yet. | Technical |
| `C-07` | GPL-3.0 attribution headers in `senior-rules/` must be preserved when redistributing. | Legal |
| `C-08` | No business requirement may be invented to fill a document (SYS-03, GEN-03). | Rule |

# Lessons Learned

| # | Lesson | Source |
|---|---|---|
| `L-01` | The three source repositories are **advisory knowledge**, not authority. Their `MUST` statements conflict with each other and with this project's constraints; the authority hierarchy in `ENTRY.md` §9 resolves conflicts. | Phase 00 conflict analysis |
| `L-02` | Source A's `ENTRY.md` response format demands an "Implementation Plan" even when no requirements exist — fill it with pointers to Phase 01/02 artifacts rather than inventing content. | Source A conflict analysis |
| `L-03` | Source B's Skill 00 claims root authority ("No agent shall bypass it"). It is a **routing mechanism, not the authority** — the ADMR rules layer outranks it. | Source B conflict analysis |
| `L-04` | Source B Skill 02 §16 explicitly invites the agent to "fill in gaps" it identified. That is a direct fabrication licence and is **prohibited** here by SYS-03. | Source B conflict analysis |
| `L-05` | Source A contains two incompatible classification taxonomies (`CRITICAL/HIGH/MEDIUM/LOW` vs `Beginner/Intermediate/Advanced/Master`) and its risk bands leave scores 10, 11, 17, 18, 19 unassigned. Do not adopt the gap-ridden bands. | Source A conflict analysis |
| `L-06` | Template numbers in the source skills (99.9% uptime, 10,000 concurrent users, "$500,000 impact") are **examples**, never requirements. Tag them `EXAMPLE` if reused. | Source A conflict analysis |
| `L-07` | The ADMR validator enforces a `mind_map.md` filename that differs from this project's `mindmap.md`. Resolve by adding a documented alias, never by editing the validator. | Phase 00 (finding F-001) |
| `L-08` | The npm ADMR installer would copy `.gitignore`, `.gitattributes`, `package.json` and `scripts/` into `senior-rules/`, four files whose first line is not `Kimi` — which would fail the validator's own signature check. Manual, selective vendoring is safer than the installer. | Phase 00 (finding F-002) |

# Anti-Patterns to Avoid

| # | Anti-pattern | Why | Prevention |
|---|---|---|---|
| `AP-01` | Claiming `DONE` without pasted raw command output | GEN-03 / DOD-10 — the single most serious failure mode | Evidence in session file before any claim |
| `AP-02` | Filling a document's placeholders with plausible-sounding invented requirements | SYS-03 — fabricates requirements | Leave `OPEN QUESTION`; never guess |
| `AP-03` | Treating a `PROPOSED` stack choice as a decision | Converts assumption into fact | ADR in `docs/decisions/` |
| `AP-04` | Writing documentation in a separate later commit | DOC-05 — docs drift immediately | Same commit, always |
| `AP-05` | Jumping to business code because governance feels slow | Violates SYS-01 | Check `development_phases_entry.md` first |
| `AP-06` | Organizing the roadmap as Phase 1 = Violations, Phase 2 = Licensing… | Those are **features**, not SDLC phases | Use the 9-phase SDLC model in `development_phases_entry.md` |
| `AP-07` | Creating duplicate governance copies under `docs/` | C4 divergence, two sources of truth | Root is canonical (C-04) |
| `AP-08` | Silently defaulting on a material ambiguity | GEN-03 risk — a guess presented as a decision | COM-01: stop, ask, then build |
| `AP-09` | Editing `senior-rules/` to make the validator pass | ADP-03 — invalidates the rules layer | Fix the project, never the rules |
| `AP-10` | Reporting enterprise metrics (SOC 2, 99.99% uptime, 7-year retention) as project targets | Inapplicable to coursework; unfalsifiable claims | Mark `NOT APPLICABLE` with a reason |
| `AP-11` | Loading every skill at session start | Context bloat, contradictory guidance | Load per phase (`AGENTS.md` skill table) |
| `AP-12` | Dead UI elements / unwired buttons | DOD-05 / IMP-01 — blocks completion | Automated inventory scan (from Phase 03) |

# Session Recovery Context

**Resume in any new session like this:**

1. Read `ENTRY.md` → project, active phase, blockers.
2. Read `session_track.md` → latest `OPEN` row → linked session file.
3. Read `development_phases_entry.md` → active phase + exit gate status.
4. Read the active phase's `TODO.md` in `docs/phases/phase-NN-*/`.
5. Read `RULES_HINTS.md` → real commands/paths for this project.
6. Re-run the validator yourself: `python senior-rules/validators/validate.py .`
   — **never trust the previous session's claims**; verify against the repo (`core/02` §2.4).
7. Determine `DONE` / `REMAINING` / `BLOCKED`, pick one scope, execute only that scope.

**Current resume point:** `docs/sessions/session-001.md` · next task = **PHASE 01 —
Requirements & Domain Analysis** (do not start automatically during Phase 00).

**Known blocker, re-checked:** `BLK-01` — **`CLOSED`** (appendix restored verbatim; see
*Permanent Project Management Methodology* + `Audit.md` `F-004`). Remaining Phase 00-relevant
blockers: **none** — `F-005`/`F-006`/`F-012` are `DEFERRED BY PHASE DESIGN` (Phases 01/01-02/03).

---

# Permanent Project Management Methodology

> **STATUS: `RESOLVED` — `BLK-01` closed 2026-09-26 (reconciliation session).**
>
> The complete **APPENDIX: PROJECT WHITEBOARD METHODOLOGY** is inserted below **verbatim**
> — no summary, no paraphrase, no invented section, no part removed.

## APPENDIX: PROJECT WHITEBOARD METHODOLOGY

APPENDIX: PROJECT WHITEBOARD METHODOLOGY
*Follow these overarching operational guidelines throughout the project lifecycle.*

**1. Initial Steps & Daily Workflow (Right Panel)**
*  Analysis & Foundation: Always navigate to the `docs/` directory to conduct analysis. Establish and approve the core execution plan (Architecture Model).
*  Daily Kickoff: Begin every work session by assessing the project state—understand what has been completed and what is pending.
*  Execution Start:
    * Identify missing tasks for the current Phase.
    * Gather and inventory all execution files related to the specific Phase.
    * Audit and review the `Todo` lists specific to the current Phase.
*  Delivery & Finalization:
    * Select a specific Phase to focus on.
    * Build the software components for that Phase.
    * Update, compile, and synchronize all Markdown (`.md`) documentation files accordingly.

**2. Core Reference Files & System Structure (Center Panel)**
*  **Primary Reference Files (`.md`):** Must consistently maintain `mindmap.md` (concept mapping), `Audit.md` (audit & review logging), and `memory.md` (cumulative system context).
*  **Tracking & Routing:** Maintain a clear task-tracking structure, plan UI distributions (Home, About, etc.), configure SEO standards, and maintain an inventory of completed files.

**3. Documentation Folder Specifications (`docs/` - Left Panel)**
*  **Analysis & Design Files:** Must include the Implementation Plan, Use Case Scenarios, Use Case Actions, Flow of Action, Flow of Events, Data Flow, Website Structure, and UI/UX Specifications.
*  **Mandatory Additions:** Ensure all other required `.md` files are present, prominently feature the `architecture.md` file, and maintain a dedicated `todo_[phase].md` file for every single development phase.

---

> **Provenance & verbatim-integrity record (annotation — not part of the appendix body):**
>
> - **Source used:** `D:\IT-Level-4\IT-Level4-part1\course\Systems-Integration-and-Architecture-course\lab\Traffic-and-Transport-Management-System\memory.md` §8, which is self-identified there as *"VERBATIM COPY — permanent operational law. Do not edit, summarize, or paraphrase. This is the full appendix from the project initialization command, preserved exactly."*
> - **Why a source was needed:** the appendix text was not present in the reconciliation session's conversation context, in this repository, or in the session/temp storage; `CF-07` (0 matches across the three external source repos) remains a true record of *those* repos.
> - **Corroboration:** an independent earlier verification run logged 10 signature phrases from the initialization command; **9 of 10 matched this text exactly** (the 10th, `Mandatory Additions: Ensure all other required`, is present at the final bullet above — that check had targeted a different file).
> - **Trailing instruction text preserved verbatim from the same source line** (prompt text that runs on after the appendix's last sentence in that copy; it is the prompt's `memory.md` description + copy directive, not methodology body): *"…maintain an inventory of completed files.`memory.md: Initialize the cumulative system context, defining the tech stack, core objectives, and guiding engineering rules. CRITICAL: You must copy the entire "APPENDIX: PROJECT WHITEBOARD METHODOLOGY" from this prompt directly into memory.md so it remains the permanent operational law for all future sessions.`"*
> - Nothing above the line was summarized, rewritten or removed (`GEN-03`, `SYS-03`).
