# all_in_one_track.md — High-Level Project Timeline

> One place to see the whole project: initialization → requirements → architecture →
> implementation → integration → testing → security → reporting → final delivery.
> Each milestone links to its phase and its artifacts.
>
> Governing rules: `DOC-04` (roll-up linkage, no orphan docs), `AUD-04` (Done/Remaining/Next).
> Authoritative phase detail lives in [`development_phases_entry.md`](development_phases_entry.md).

---

## Legend

| Symbol | Meaning |
|---|---|
| ✅ | Completed with evidence |
| 🟦 | Active |
| ⬜ | Not started |
| ⛔ | Blocked (reason given) |

---

## M0 — Project initialization & governance ✅ 🟦

| | |
|---|---|
| **Phase** | [PH-00 — Initialization & Governance](development_phases_entry.md) |
| **Artifacts** | [Phase 00 TODO](docs/phases/phase-00-initialization/TODO.md) · [PLAN](docs/phases/phase-00-initialization/PLAN.md) · [AUDIT](docs/phases/phase-00-initialization/AUDIT.md) |
| **Delivers** | Repo init, governance set, docs architecture, `.opencode/`, `senior-rules/`, `RULES_HINTS.md`, phase + session tracking, traceability structure |
| **Status** | 🟩 Phase 00 `PASSED` (`GO`, 41/41 — reconciled 2026-09-26) · next `M1`/Phase 01 awaits user instruction |
| **Evidence** | [session-001](docs/sessions/session-001.md) |

## M1 — Requirements baseline ⬜

| | |
|---|---|
| **Phase** | [PH-01 — Requirements & Domain Analysis](development_phases_entry.md) |
| **Artifacts** | [Phase 01 TODO](docs/phases/phase-01-analysis/TODO.md) · [PLAN](docs/phases/phase-01-analysis/PLAN.md) · [AUDIT](docs/phases/phase-01-analysis/AUDIT.md) |
| **Delivers** | [01-requirements](docs/01-requirements.md) · [02-use-cases](docs/02-use-cases.md) · [03-use-case-actions](docs/03-use-case-actions.md) · [04-flow-actions](docs/04-flow-actions.md) · [05-flow-events](docs/05-flow-events.md) · [06-data-flow](docs/06-data-flow.md) · [16-glossary](docs/16-glossary.md) · [17-traceability-matrix](docs/17-traceability-matrix.md) |
| **Exit gate** | Stakeholders identified; 0 unresolved ambiguities; traceability complete; no fabricated requirements |

## M2 — Architecture & integration design ⬜

| | |
|---|---|
| **Phase** | [PH-02 — Architecture & Integration Design](development_phases_entry.md) |
| **Artifacts** | [Phase 02 TODO](docs/phases/phase-02-architecture/TODO.md) · [PLAN](docs/phases/phase-02-architecture/PLAN.md) · [AUDIT](docs/phases/phase-02-architecture/AUDIT.md) |
| **Delivers** | [architecture.md](architecture.md) delta · ADRs in [docs/decisions](docs/decisions/) · [09-database](docs/09-database.md) · [10-api-specification](docs/10-api-specification.md) · [11-integration-specification](docs/11-integration-specification.md) · [12-security-specification](docs/12-security-specification.md) · [14-quality-attributes](docs/14-quality-attributes.md) |
| **Exit gate** | Architecture review passed; threat model defined; technology matrix conforms to [RULES_HINTS](RULES_HINTS.md) §2; every `PROPOSED` accepted or rejected via ADR |

## M3 — Technical foundation ⬜

| | |
|---|---|
| **Phase** | [PH-03 — Technical Foundation](development_phases_entry.md) |
| **Artifacts** | [Phase 03 TODO](docs/phases/phase-03-foundation/TODO.md) · [PLAN](docs/phases/phase-03-foundation/PLAN.md) · [AUDIT](docs/phases/phase-03-foundation/AUDIT.md) |
| **Delivers** | Toolchain, CI, lint/test/coverage, migrations with rehearsed rollback, secret + dependency scanning, Docker base, auth skeleton, permissions matrices |
| **Exit gate** | Build/lint/test green; scans runnable & clean; rollback rehearsed; **`RULES_HINTS.md` §3 commands become AVAILABLE** |

## M4 — Core traffic domain implementation ⬜

| | |
|---|---|
| **Phase** | [PH-04 — Core Traffic Domain](development_phases_entry.md) |
| **Artifacts** | [Phase 04 TODO](docs/phases/phase-04-core-traffic/TODO.md) · [PLAN](docs/phases/phase-04-core-traffic/PLAN.md) · [AUDIT](docs/phases/phase-04-core-traffic/AUDIT.md) |
| **Delivers** | Drivers, vehicles, licenses, violations, fines, penalty points, accidents, incidents, monitoring, signals, reporting, notifications — all in one SDLC phase, not as separate "phases" |
| **Exit gate** | DOD G1–G9 green; 0 dead elements; full CORE-03 artifact set present |

## M5 — External system integration ⬜

| | |
|---|---|
| **Phase** | [PH-05 — External System Integration](development_phases_entry.md) |
| **Artifacts** | [Phase 05 TODO](docs/phases/phase-05-integration/TODO.md) · [PLAN](docs/phases/phase-05-integration/PLAN.md) · [AUDIT](docs/phases/phase-05-integration/AUDIT.md) |
| **Delivers** | Synchronous REST adapters + asynchronous event consumers + contract tests + dead-letter handling |
| **Exit gate** | Contract tests green per **confirmed** boundary only; 0 open `CRITICAL`/`HIGH` |

## M6 — UI, dashboards & reporting ⬜

| | |
|---|---|
| **Phase** | [PH-06 — UI / Dashboard / Reporting](development_phases_entry.md) |
| **Artifacts** | [Phase 06 TODO](docs/phases/phase-06-reporting-ui/TODO.md) · [PLAN](docs/phases/phase-06-reporting-ui/PLAN.md) · [AUDIT](docs/phases/phase-06-reporting-ui/AUDIT.md) |
| **Delivers** | [07-website-structure](docs/07-website-structure.md) · [08-ui-ux-specification](docs/08-ui-ux-specification.md) baselined; wired UI; dashboards; reports |
| **Exit gate** | 0 dead elements (automated scan); WCAG 2.1 AA = 0 serious; no `alert()`/`confirm()`/`prompt()` |

## M7 — Testing, security & performance ⬜

| | |
|---|---|
| **Phase** | [PH-07 — Testing / Security / Performance](development_phases_entry.md) |
| **Artifacts** | [Phase 07 TODO](docs/phases/phase-07-quality-security/TODO.md) · [PLAN](docs/phases/phase-07-quality-security/PLAN.md) · [AUDIT](docs/phases/phase-07-quality-security/AUDIT.md) |
| **Delivers** | Executed [13-testing-strategy](docs/13-testing-strategy.md); security audit; performance results; QA attribute results |
| **Exit gate** | 100% tests pass, 0 skips; coverage ≥ 80% / 100% critical; 0 `CRITICAL`/`HIGH` security findings; budgets met with numbers |

## M8 — Final integration, documentation & delivery ⬜

| | |
|---|---|
| **Phase** | [PH-08 — Final Integration / Documentation / Delivery](development_phases_entry.md) |
| **Artifacts** | [Phase 08 TODO](docs/phases/phase-08-final-delivery/TODO.md) · [PLAN](docs/phases/phase-08-final-delivery/PLAN.md) · [AUDIT](docs/phases/phase-08-final-delivery/AUDIT.md) |
| **Delivers** | Full documentation consistency pass (AUD-06), delivery package, lessons learned, final end-to-end traceability |
| **Exit gate** | Every doc consistent with code; validator green; all `CONFIRMED` requirements traceable end-to-end; **0 open `CRITICAL`/`HIGH` project-wide**; sign-off |

---

## Cross-cutting threads (run through every phase, not milestones)

| Thread | Home | Rule |
|---|---|---|
| Security | `docs/12-security-specification.md` + per-phase `security-audit-<phase>.md` | `SEC-04`, precedence `SEC` first |
| Audit & findings | [`Audit.md`](Audit.md) | `AUD-01`…`AUD-06` |
| Traceability | [`docs/17-traceability-matrix.md`](docs/17-traceability-matrix.md) | `SYS-05` |
| Risk | [`docs/15-risk-register.md`](docs/15-risk-register.md) | weekly review once active |
| Sessions & recovery | [`session_track.md`](session_track.md) + `docs/sessions/` | `SES-01`…`SES-05` |
| Governance changes | [`CHANGELOG.md`](CHANGELOG.md) | `DOC-06` |
| Cumulative memory | [`memory.md`](memory.md) | updated on durable change only |

---

## Current position

**You are here: M0 (Phase 00) — `PASSED` (`GO`, 41/41).** `M1`/Phase 01 is next but must
not start without explicit user instruction. Deferred, still open: `F-005` → 01,
`F-006` → 01/02, `F-012` → 03.
Next milestone: **M1 (Phase 01)** — do not start it until Phase 00's gate is resolved.

---

## Related documents

- [`development_phases_entry.md`](development_phases_entry.md) — authoritative phase registry
- [`docs/phases/README.md`](docs/phases/README.md) — phase index
- [`ENTRY.md`](ENTRY.md) — orientation & next task
- [`Audit.md`](Audit.md) — findings & remediation waves
