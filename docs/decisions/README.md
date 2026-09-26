# docs/decisions — Architecture Decision Records (ADRs)

| Field | Value |
|---|---|
| **Purpose** | Hold every architecture decision: context, decision, consequences, alternatives rejected, and how compliance is verified. |
| **Scope** | Architecture and integration decisions only. Process decisions go in [`../Audit.md`](../../Audit.md) §6; requirement decisions go in the Phase 01 baseline. |
| **Current Status** | **0 ADRs.** Registry below is empty. |
| **Phase** | Created Phase 00; populated in Phase 02 (and on any later architecture change) |
| **Last updated** | 2026-09-26 |

---

## Why this registry exists

`core/10_architecture.md` §10.3: *"New patterns need an ADR (Architecture Decision Record):
context, decision, consequences."*
`RULES_HINTS.md` **SYS-06**: *an architecture decision may not be stated as fact without an
ADR.* Until an ADR reaches `Accepted`, the corresponding choice stays `PROPOSED`.

The project specification is explicit: architecture decisions must be recorded as ADRs
**rather than silently turning assumptions into facts.**

## ADR template

Copy `TEMPLATE_adr.md` and name the file `ADR-NNNN-<slug>.md`.

Required sections: **Status** (`Proposed` / `Accepted` / `Deprecated` / `Superseded by
ADR-YYYY`) · **Context** · **Decision** · **Consequences** (positive, negative, risks) ·
**Alternatives considered** (and why rejected) · **Compliance** (how the decision is verified).

## ADR register

| ADR | Title | Status | Date | Supersedes |
|---|---|---|---|---|
| *— none yet —* | | | | |

**Accepted ADRs: 0.**

## Pending decisions that will need ADRs (`PROPOSED`)

| # | Decision | Source | Target phase |
|---|---|---|---|
| 1 | Architectural style: modular monolith + integration layer + event-driven | `../architecture.md` §1 (`AQ-01`) | 02 |
| 2 | Backend framework (NestJS) | `../architecture.md` §2 | 02 |
| 3 | Frontend framework (React + TypeScript) | `../architecture.md` §2 | 02 |
| 4 | Database engine (PostgreSQL) + ORM + migration tool | `../docs/09-database.md` §7 | 02 |
| 5 | API style + contract format + versioning + error format | `../docs/10-api-specification.md` §7 | 02 |
| 6 | Message broker (RabbitMQ) + delivery guarantees + outbox | `../docs/05-flow-events.md` §10, `AQ-03` | 02 |
| 7 | Authentication (JWT) + authorization (RBAC) model | `../docs/12-security-specification.md` §7 | 02 |
| 8 | Containerization (Docker / Docker Compose) | `../architecture.md` §2 | 02/03 |
| 9 | Which external-system boundaries to implement, and via what adapters | `../docs/11-integration-specification.md` §9 | 02 |
| 10 | Test toolchain, coverage tooling, CI platform | `../docs/13-testing-strategy.md` §10 | 03 |

> None of these is decided. All remain `PROPOSED`.

## Rules for this directory

1. One decision per file; never edit history — supersede instead.
2. Status must be one of the four values above.
3. An ADR with no `Compliance` section is incomplete (`core/10`).
4. If a decision deviates from `RULES_HINTS.md` §2's proposed stack, that is a **user
   decision** — do not switch stacks silently (`core/03`, technology-recommendation rule).
5. `CHANGELOG.md` records accepted ADRs (`DOC-06`, `VCS-05`).

## Traceability references

- **Upstream:** [`../architecture.md`](../../architecture.md) §6 ·
  [`../RULES_HINTS.md`](../../RULES_HINTS.md) §2 ·
  [`../senior-rules/core/10_architecture.md`](../../senior-rules/core/10_architecture.md)
- **Downstream:** [`../CHANGELOG.md`](../../CHANGELOG.md) ·
  [`../development_phases_entry.md`](../../development_phases_entry.md) (Phase 02 gate) ·
  [`../Audit.md`](../../Audit.md) §6 (decision traceability)

## Related documents

- [`../architecture.md`](../../architecture.md)
- [`../Audit.md`](../../Audit.md)
- [`../phases/phase-02-architecture/PLAN.md`](../phases/phase-02-architecture/PLAN.md)
