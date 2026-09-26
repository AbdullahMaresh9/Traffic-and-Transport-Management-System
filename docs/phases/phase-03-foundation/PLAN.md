# Implementation Plan — phase-03-foundation

- Phase: **PH-03 — Technical Foundation** · Slug: `phase-03-foundation` · Status: **`NOT STARTED`**
- Rules version: **2.0.0** · Dependencies: `PH-02` (must be `PASSED`)
- Owner: AI agent (OpenCode) · Human owner: **`OPEN QUESTION`** (no supervisor identified, `F-006`)

---

## 1. Objective & scope

### Objective (`CONFIRMED` — from `../../../development_phases_entry.md`)

Create the toolchain and skeleton that later phases build on: repository structure, CI, lint/test/coverage tooling, migration tooling, secret and dependency scanning, Docker base, auth skeleton.

### Out of scope

Anything not derived from the approved requirements baseline (`SYS-03`). Phases 00–02 contain no application implementation (`SYS-01`, `SYS-08`).

## 2. Inputs

| Input | Status |
|---|---|
| Previous phase outputs | `CONFIRMED` prerequisite |
| Rule set + `../../../RULES_HINTS.md` | `CONFIRMED` prerequisite |
| `../../../architecture.md` | `CONFIRMED` prerequisite |

## 3. Outputs

| Output | Status |
|---|---|
| Repository structure | `NOT STARTED` |
| CI pipeline | `NOT STARTED` |
| Lint/test/coverage tooling | `NOT STARTED` |
| Migration tooling + rollback rehearsal evidence | `NOT STARTED` |
| Secret + dependency scanning (closes `F-012`) | `NOT STARTED` |
| Docker base | `NOT STARTED` |
| Auth skeleton | `NOT STARTED` |
| Implemented commands in `../../../RULES_HINTS.md` §3 | `NOT STARTED` |
| `permissions-<feature>.md` | `NOT STARTED` |

## 4. Activities

| # | Activity | Method | Output | Status |
|---|---|---|---|---|
| A1 | Define repository structure per architecture | Implementation | source tree | `NOT STARTED` |
| A2 | Set up build + lint + test + coverage tooling | Tooling | runnable commands | `NOT STARTED` |
| A3 | Set up CI pipeline | Tooling | CI config | `NOT STARTED` |
| A4 | Set up migration tooling and rehearse rollback | Tooling + drill | rollback rehearsal evidence | `NOT STARTED` |
| A5 | Set up secret scanning and dependency scanning | Security tooling | scanners (closes F-012) | `NOT STARTED` |
| A6 | Create Docker base image | Implementation | Dockerfile | `NOT STARTED` |
| A7 | Create auth skeleton (no business data) | Implementation | auth skeleton | `NOT STARTED` |
| A8 | Update `../../../RULES_HINTS.md` §3 in the same commit (replace NOT YET AVAILABLE) | Documentation | §3 commands runnable | `NOT STARTED` |
| A9 | Run gates G1–G7 + validator, evaluate exit gate, commit | `GEN-04` + `validate.py` | AUDIT.md evidence | `NOT STARTED` |

## 5. Phase rules

- `GEN-04`/`DOD-10`: paste raw gate output; no completion claim without it.
- `SEC-01`: secrets never committed; scanners must exist and run.
- `DOC-05`: `RULES_HINTS.md` §3 updated in the same commit as the tooling.

## 6. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| Scanners added late → secrets or CVEs slip in | `HIGH` | Scanning is a Phase 03 gate item (closes F-012) |
| Toolchain churn delays domain work | `MEDIUM` | Keep tooling minimal, academic-scope driven |

## 7. Exit criteria

See [`AUDIT.md`](AUDIT.md) §5 for the evaluated checklist with evidence. The phase may not be reported `PASSED`/`COMPLETE` while any item is `FAIL` or `BLOCKED` (`DOD-10`, `AUD-02`).

## 8. Documentation artifacts (CORE-03)

Produced/updated in this phase per `../../../senior-rules/core/03_phase_documentation.md`; each artifact is listed in [`AUDIT.md`](AUDIT.md) with its status.

---

## Roll-up

- TODO: [`TODO.md`](TODO.md) · Audit: [`AUDIT.md`](AUDIT.md) · Index: [`_index.md`](_index.md)
- Phases README: [`../README.md`](../README.md) · Rules adapter: [`../../../RULES_HINTS.md`](../../../RULES_HINTS.md)
