# 12 — Security Specification (Architecture Foundation)

| Field | Value |
|---|---|
| **Purpose** | Be the project's **supreme security reference**: record the security posture, the mandatory baseline, the assets and trust boundaries, and the questions Phase 02 must resolve. |
| **Scope** | Foundation only — posture, baseline obligations, attack-surface hypotheses, open questions. **No threat model yet.** |
| **Current Status** | `PROPOSED` foundation; baseline obligations are `CONFIRMED` (they come from `SEC-*` rules). **Threat model: not written** (Phase 02). |
| **Phase** | 00 foundation → fully specified in **Phase 02**, audited every phase |
| **Last updated** | 2026-09-26 |

> Per `core/05`, this document is supreme for security; where it is stricter than the ADMR
> baseline, **the stricter rule wins** (`GEN-07`).

---

## 1. Purpose

Fix the security baseline before any code exists, so security is designed in rather than
bolted on (`SEC-*` precedence: security beats everything).

## 2. Scope

- **In:** security posture, mandatory baseline (`SEC-01`…`SEC-10`), candidate assets,
  trust boundaries, logging/privacy obligations, open questions, per-phase audit plan.
- **Out:** threat model, STRIDE analysis, detailed controls, security test cases
  (Phase 02 / Phase 07).

## 3. Security posture (`CONFIRMED` doctrine)

Adopted verbatim in spirit from `core/05` / Source A `06`:

| Principle | Meaning here |
|---|---|
| Assume breach | design as if attackers are already inside |
| Defense in depth | no single point of failure |
| Least privilege | minimum access necessary |
| Security by design | built in, not bolted on |
| Zero trust | verify everything, trust nothing |
| Deny by default | default answer is 403 |

## 4. Mandatory baseline (`CONFIRMED` obligations)

| ID | Requirement | Rule | Phase 00 status |
|---|---|---|---|
| `SEC-01` | **No secrets in the repo.** `.env*` gitignored day zero; `.env.example` with placeholders when config exists; secret scanning pre-commit + CI. | `SEC-01`, `core/05` §5.1 | Partially: `.gitignore` in place; **scanner not installed** (`F-012`) |
| `SEC-02` | AuthN on every non-public endpoint; AuthZ checked **server-side per operation** against the permissions matrix; every role×action row has an enforcement test. | `SEC-02` | Not applicable — no endpoints; role set unknown (`OQ-06`) |
| `SEC-03` | Input validation + parameterized queries everywhere; injection defenses (SQL/NoSQL/command/template) at trust boundaries. | `SEC-03` | Not applicable — no code |
| `SEC-04` | A `security-audit-<phase>.md` per phase: assets, STRIDE-lite threat model, attack surface, findings table, mitigations, residual risk — **0 open `CRITICAL`/`HIGH` at phase close.** | `SEC-04` | Phase 00 security audit: see §8 |
| `SEC-05` | Logs never contain secrets or un-redacted PII. | `SEC-05`, `LOG-02` | Not applicable — no logs |
| `SEC-06` | Pinned dependencies + lockfile; vulnerability scan = 0 exploitable `CRITICAL`/`HIGH`, or documented exception with expiry. | `SEC-06` | Not applicable — **no dependency manifest exists** (`F-012`) |
| `SEC-07` | Security headers (CSP, HSTS, X-Frame-Options…), minimal CORS allowlist, rate limiting, brute-force protection on auth surfaces. | `SEC-07` | Not applicable — no exposed surface |
| `SEC-08` | TLS in transit; encryption at rest for sensitive data; passwords hashed with a slow, salted algorithm. | `SEC-08` | Not applicable |
| `SEC-09` | Automated, tested-restoreable backups; documented RPO/RTO. | `SEC-09` | `OPEN QUESTION` — no RPO/RTO defined (`OQ-DB-*`) |
| `SEC-10` | Security incident register: every incident, near-miss and exception logged with disposition. | `SEC-10` | Register created in [`../Audit.md`](../Audit.md); 0 entries |
| `LOG-01` | Relational activity log schema: `users`, `user_sessions`, `actions`, `errors`, `activity_stats`. | `LOG-01` | Doctrine recorded in [`09-database.md`](09-database.md) §5 |
| `LOG-02` | PII redaction + secret scrubbing before persistence; documented retention & access control. | `LOG-02` | Retention policy `OPEN QUESTION` |
| `LOG-03` | Fail-safe logging: a logging failure must never break the business transaction. | `LOG-03` | Not applicable — no code |

## 5. Candidate assets (`PROPOSED`)

| Asset | Sensitivity | Notes |
|---|---|---|
| Citizen / driver personal data | **High (PII)** | redaction + retention required (`LOG-02`) |
| Driving license & penalty-point records | High | lifecycle-bearing, enforcement-relevant |
| Payment records | **High** | money-moving → critical path |
| Authentication credentials / JWT signing keys | **Critical** | never in repo (`SEC-01`) |
| Audit trail | High | must be tamper-evident for auditability objective |
| Traffic signal / sensor control data | Medium-High | safety-relevant if control is in scope (`MQ-02`) |
| Reporting aggregates | Low-Medium | |

## 6. Candidate trust boundaries (`PROPOSED`)

1. Browser ↔ API application
2. API application ↔ PostgreSQL
3. API application ↔ RabbitMQ
4. API application ↔ each `EXT-*` boundary (6 candidates, all unconfirmed)
5. Operator/admin console ↔ internal services
6. Log pipeline ↔ business transaction (must fail safe, `LOG-03`)

## 7. Authentication & authorization (`PROPOSED`)

| Decision | Status |
|---|---|
| JWT-based authentication | `PROPOSED` — needs ADR |
| RBAC authorization | `PROPOSED` — **role set unknown** (`OQ-06`) |
| Session model, token lifetime, refresh strategy | `OPEN QUESTION` |
| MFA | `OPEN QUESTION` (Source A marks it mandatory for sensitive accounts; not confirmed here) |
| Permissions matrix artifact | required by `IMP-03` — **cannot be written until roles are known** |

## 8. Phase 00 security audit (`SEC-04` — scoped honestly)

| Field | Value |
|---|---|
| Assets | none in the system yet (no data, no endpoints, no credentials) |
| Attack surface | **repository contents only** |
| Threat model | not applicable at Phase 00 — would be fabricated |
| Findings | `F-012` (`HIGH`) — no secret scanner, no dependency scanner, no CI, no branch protection |
| Secrets in repo | **0** (verified: no `.env`, no keys, no tokens committed) |
| Residual risk | low for a governance-only phase; enforcement gaps tracked as `F-012` |
| Open `CRITICAL`/`HIGH` | **1** — `F-012` (`HIGH`). No `CRITICAL`. |

> Honest note: because `F-012` is `HIGH` and open, this audit is **not** a clean pass.
> It is `INCOMPLETE`, deferred by design to Phase 03 where the toolchain is created.

## 9. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-SEC-01` | What is the complete RBAC role set and permission matrix? (`OQ-06`) | 01/02 |
| `OQ-SEC-02` | What personal data does the system actually hold, and what is the retention period? | 01 |
| `OQ-SEC-03` | Is MFA required for any role? | 01/02 |
| `OQ-SEC-04` | What are the RPO/RTO targets? (`SEC-09`) | 01/02 |
| `OQ-SEC-05` | Are there applicable data-protection obligations (student data, simulated real identities)? | 01 |
| `OQ-SEC-06` | Does the system *control* traffic signals (safety-relevant) or only monitor? (`MQ-02`) | 01 |
| `OQ-SEC-07` | Which secret/dependency scanners will be adopted in Phase 03? | 03 |

## 10. Per-phase security audit plan (`SEC-04`)

| Phase | `security-audit-<phase>.md` required? |
|---|---|
| 00 | Yes — see §8 (scoped to repository contents) |
| 01 | Yes — requirements/security-requirements review |
| 02 | Yes — **threat model (STRIDE-lite), attack surface, security design** |
| 03 | Yes — toolchain, secrets, dependency scanning, auth skeleton |
| 04–06 | Yes — per-phase attack-surface delta |
| 07 | Yes — full security test suite, 0 `CRITICAL`/`HIGH` |
| 08 | Yes — final consolidated security sign-off |

## 11. Traceability references

- **Upstream:** [`../senior-rules/RULES.md`](../senior-rules/RULES.md) (`SEC-*`, `LOG-*`) ·
  [`../senior-rules/core/05_security.md`](../senior-rules/core/05_security.md) ·
  [`01-requirements.md`](01-requirements.md) (`NFR-CAT-04`)
- **Downstream:** [`09-database.md`](09-database.md) (encryption, PII) ·
  [`10-api-specification.md`](10-api-specification.md) (`API-R-03`…`API-R-08`) ·
  [`11-integration-specification.md`](11-integration-specification.md) (trust boundaries) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (security suite) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 12. Related documents

- [`../Audit.md`](../Audit.md) — findings register & security incident register
- [`../RULES_HINTS.md`](../RULES_HINTS.md) — this project's security bindings
- [`12-security-specification.md`](12-security-specification.md) (this file)
- [`15-risk-register.md`](15-risk-register.md)
- [`../phases/phase-07-quality-security/PLAN.md`](phases/phase-07-quality-security/PLAN.md)
