# RULES_HINTS — System Adapter (binds ADMR to this system)

> Adapter required by ADP-01/ADP-02. Created in **Phase 00** from
> `senior-rules/adapters/RULES_HINTS.template.md`. Core rule files under `senior-rules/`
> are **never modified** (ADP-03). Framework- and project-specific bindings live ONLY here.

## 1. System identity

- **Name:** Traffic and Transport Management System (TTMS)
- **Version:** `0.0.0` — no application release exists yet (Phase 00 = governance only)
- **Rules version pinned:** `2.0.0` (value of `senior-rules/VERSION`)
  - **DISCREPANCY (recorded, see `Audit.md` F-003):** `senior-rules/CHANGELOG.md` shows a
    latest entry of `[2.1.0]` while `senior-rules/VERSION` contains `2.0.0`. The `VERSION`
    file is treated as authoritative. Reported, not silently reconciled (GEN-08).
- **Repository:** https://github.com/AbdullahMaresh9/Traffic-and-Transport-Management-System.git
- **Default / only branch:** `main`
- **Nature:** Academic engineering project — Fourth-Year Information Technology,
  course *Systems Integration and Architecture*.

## 2. Stack

> Everything below is **PROPOSED** and remains provisional until validated in **Phase 02**
> (see `architecture.md` and `docs/decisions/`). Nothing here is a confirmed requirement.

| Layer | Proposed choice | Status |
|---|---|---|
| Language / runtime | TypeScript (Node.js) | PROPOSED |
| Backend framework | NestJS | PROPOSED |
| Frontend framework | React + TypeScript | PROPOSED |
| Database | PostgreSQL | PROPOSED |
| Cache / queue / broker | RabbitMQ | PROPOSED |
| API style | REST + OpenAPI | PROPOSED |
| AuthN / AuthZ | JWT + RBAC | PROPOSED |
| Infra | Docker / Docker Compose (local) | PROPOSED |

No application code, manifest, lockfile, container or database exists yet.

## 3. Commands (must all exist and run green)

| Purpose | Command | Availability |
|---|---|---|
| Structural validation | `python senior-rules/validators/validate.py .` | **AVAILABLE — verified** (evidence in `docs/phases/phase-00-initialization/AUDIT.md`) |
| Structural validation (alt.) | `npm run validate` | **AVAILABLE — verified** (root `package.json`) |
| Git status / history | `git status`, `git log --oneline` | **AVAILABLE** |
| Build | — | **NOT YET AVAILABLE — PHASE 00** |
| Lint | — | **NOT YET AVAILABLE — PHASE 00** |
| Unit tests | — | **NOT YET AVAILABLE — PHASE 00** |
| Full test suite | — | **NOT YET AVAILABLE — PHASE 00** |
| Coverage report | — | **NOT YET AVAILABLE — PHASE 00** |
| Migration run | — | **NOT YET AVAILABLE — PHASE 00** |
| Migration rollback (rehearsal) | — | **NOT YET AVAILABLE — PHASE 00** |
| Secret scan | — | **NOT YET AVAILABLE — PHASE 00** (`.gitignore` deny-list for `.env*` is in place) |
| Dependency vulnerability scan | — | **NOT YET AVAILABLE — PHASE 00** (no dependency manifest exists) |
| Dead-element scan | — | **NOT YET AVAILABLE — PHASE 00** |
| Benchmark | — | **NOT YET AVAILABLE — PHASE 00** |

> **RULE (binding):** Never present a `NOT YET AVAILABLE — PHASE 00` command as runnable.
> When Phase 03 creates the toolchain, this table must be updated **in the same commit**
> that adds the command (DOC-05).

### Python invocation note (environment-specific, CONFIRMED)

This workspace is **Windows + PowerShell**. `python3` is **not** on PATH; `python` is
**Python 3.14.4**. The therefore-actual, verified invocation of the mandated validator is:

```
python senior-rules/validators/validate.py .
```

`python3 senior-rules/validators/validate.py .` is documented in `senior-rules/README.md`
as the generic form and will fail on this machine. This is an environment fact, not a
modification of the rule system.

## 4. Paths

- **Base dirs:** `docs/` (documentation), `docs/phases/` (per-phase), `docs/sessions/`
  (session evidence), `senior-rules/` (vendored rule system), `.opencode/` (agents + skills).
  Source dirs (`src/`, `tests/`, `app/`, …) do **not exist yet**.
- **Entry files present:** `ENTRY.md`, `RULES.md` (in `senior-rules/`), `mindmap.md`,
  `mind_map.md` (validator alias — see `Audit.md` F-001), `architecture.md`, `AGENTS.md`,
  `memory.md`, `development_phases_entry.md`, `all_in_one_track.md`, `session_track.md`,
  `CHANGELOG.md`, `RULES_HINTS.md`, `README.md`, `Audit.md`.
- **Main security spec:** `docs/12-security-specification.md` (Phase 00 skeleton; detailed
  spec due in Phase 02)
- **Main architecture file:** `architecture.md`
- **Master entry / orientation:** `ENTRY.md`
- **Operational entry for AI sessions:** `AGENTS.md`
- **Phase registry:** `development_phases_entry.md`
- **Audit framework / findings register:** `Audit.md`

## 5. Conventions

- **Branch prefix:** trunk-based off `main`; `feat/<task-id>-<slug>`, `fix/<task-id>-<slug>`,
  `chore/<slug>`, `docs/<slug>`, `security/<slug>` (VCS-01).
- **Module boundaries:** not yet defined — to be established in Phase 02 (`architecture.md`).
- **Naming:** documentation uses zero-padded ordered prefixes (`00-…` … `16-…`) under
  `docs/`; phases use `phase-NN-<slug>/`; sessions use `session-NNN.md`.
- **Env / config management:** `.env*` is gitignored from day zero (SEC-01). No `.env`
  or `.env.example` exists yet because there is no application.
- **Evidence rule:** every claim of completion is backed by raw command output pasted into
  `docs/sessions/session-NNN.md` (GEN-04) — never narrative alone.
- **Language:** project documentation is authored in English.

## 6. Overrides (may tighten, may NOT loosen without user approval)

- **Coverage:** unchanged — `>= 80%` overall, `100%` on critical paths (auth, permissions,
  money movement, core CRUD, transactions). Not yet measurable (no code).
- **Perf budgets:** unchanged — API reads p95 `<= 500 ms`; API writes p95 `<= 800 ms`;
  page interactive `<= 3 s` on throttled 4G; TTFB `<= 600 ms`; first load `<= 250 KB`
  gzipped. Not yet measurable (no code).
- **Supported locales / RTL:** `OPEN QUESTION` — **none confirmed.** No locale has been
  specified by any stakeholder. Default assumption pending Phase 01: single locale `en`,
  no RTL. Must not be treated as decided (UI-03 cannot be closed until answered).
- **Accessibility target:** unchanged — **WCAG 2.1 AA** (UI-02). To be verified with an
  automated axe/Lighthouse audit once UI exists (Phase 06).
- **Data retention / backups (SEC-09):** no production data exists; RPO/RTO definition is
  deferred to Phase 02 and is an **OPEN QUESTION**.

## 7. System-specific rules (stack-level only)

These are project additions. They tighten the core rules; they never loosen them.

- **SYS-01** — Phase 00 is a hard scope fence: **no application business functionality**
  (no entity CRUD, no business APIs, no business DB models, no business services) may be
  created before Phase 01 and Phase 02 exit gates have both explicitly passed. Violation is
  a `GEN-02` finding.
- **SYS-02** — Every requirements-, architecture-, or domain-shaped statement in any
  document must carry one of: `CONFIRMED`, `ASSUMPTION`, `PROPOSED`, `OPEN QUESTION`,
  `BLOCKED`. An unlabeled claim is treated as an unverified claim.
- **SYS-03** — Do not fabricate stakeholders, regulations, integrations, APIs, workflows,
  external systems, or technical facts. Missing information is recorded as an
  `OPEN QUESTION`, never filled in with plausible content (reinforces `GEN-03`, `COM-01`).
- **SYS-04** — Every external system named in `architecture.md` is a
  `PROPOSED INTEGRATION BOUNDARY` until validated in Phase 01/02. None is confirmed.
- **SYS-05** — Traceability chain (initialized in `docs/17-traceability-matrix.md`):
  `Requirement → User Story → Use Case → Business Rule → Domain Component → API → Database
  → Event → Integration → Test Case → Phase`. Every `CONFIRMED` major requirement must
  eventually be traceable through the full chain.
- **SYS-06** — An architecture decision may not be stated as fact without an ADR under
  `docs/decisions/`. Until Phase 02, all stack choices remain `PROPOSED`.
- **SYS-07** — `AGENTS.md` is the single operational entry point for AI sessions; it links
  out and never inlines the full skill ecosystem (load skills per phase, not wholesale).
- **SYS-08** — The Phase 00 restriction in SYS-01 expires only when
  `development_phases_entry.md` shows Phase 01 **and** Phase 02 as `PASSED`, with gate
  evidence linked from the respective `docs/phases/phase-0N-*/AUDIT.md`.

## 8. Sign-off

- **Prepared by:** AI agent (MiMo / OpenCode session) — Phase 00 bootstrap
- **Date:** 2026-09-26
- **Reviewed by:** `OPEN QUESTION` — human supervisor sign-off not yet obtained
- **Status:** `PROPOSED` pending supervisor review; in force as the execution binding of
  `senior-rules/` from Phase 00 onward.
