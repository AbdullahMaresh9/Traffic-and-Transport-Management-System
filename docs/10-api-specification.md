# 10 — API Specification (Architecture Foundation)

| Field | Value |
|---|---|
| **Purpose** | Record what is known about the API surface, the contracts it must honour, and the questions Phase 02 must answer. |
| **Scope** | Foundation only — constraints, conventions, initial proposed structure, validation needs. **No endpoint is specified.** |
| **Current Status** | `PROPOSED` foundation. **0 endpoints, 0 operations, 0 OpenAPI documents.** |
| **Phase** | 00 foundation → fully specified in **Phase 02** |
| **Last updated** | 2026-09-26 |

> Detailed endpoint design, schemas and examples belong to Phase 02. Contract-first means
> the OpenAPI document is authored **before** implementation, not after.

---

## 1. Purpose

Fix the API conventions now so that Phase 02's contract and Phase 03's tooling agree, and so
Phase 04/05 cannot invent incompatible endpoints.

## 2. Scope

- **In:** style hypothesis, mandatory API rules, proposed resource map, error-format
  decisions, versioning policy, open questions.
- **Out:** paths, methods, request/response schemas, examples, generated clients
  (Phase 02); implementation (Phase 03+).

## 3. Known context

| Item | Value |
|---|---|
| Style | REST (`PROPOSED`) |
| Contract format | OpenAPI (`PROPOSED`) |
| Base path | `PROPOSED`: `/v1/...` |
| Authentication | JWT (`PROPOSED`) |
| Authorization | RBAC (`PROPOSED`) — role set unknown |
| Endpoints existing | **0** |
| Contract tests existing | 0 |

## 4. Initial proposed resource map (`PROPOSED`)

Names only — derived from [`02-use-cases.md`](02-use-cases.md); **no path is approved**.

| Resource (candidate) | Linked use cases | Status |
|---|---|---|
| `/drivers` | UC-01 | `PROPOSED` |
| `/vehicles` | UC-02 | `PROPOSED` |
| `/licenses` | UC-03, UC-04, UC-10 | `PROPOSED` |
| `/violations` | UC-05, UC-06 | `PROPOSED` |
| `/fines` (+ `/payments`) | UC-07, UC-08 | `PROPOSED` |
| `/accidents` | UC-11, UC-12 | `PROPOSED` |
| `/incidents` | UC-13 | `PROPOSED` |
| `/monitoring/readings` | UC-14, UC-15, UC-24 | `PROPOSED` |
| `/signals` | UC-16, UC-24 | `PROPOSED` |
| `/notifications` | UC-17 | `PROPOSED` |
| `/reports` | UC-21 | `PROPOSED` |
| `/auth` | UC-18 | `PROPOSED` |
| `/admin/users`, `/admin/roles` | UC-19 | `PROPOSED` |
| `/audit` | UC-20 | `PROPOSED` |
| `/internal/identity/verify` (adapter) | UC-23 | `BLOCKED` — boundary unconfirmed |

## 5. Mandatory API rules (`CONFIRMED` as obligations)

| ID | Requirement | Rule |
|---|---|---|
| `API-R-01` | APIs are versioned; breaking change = new version, never silent breakage; deprecations announced in `CHANGELOG.md` | `IMP-07`, `core/09` §9.3 |
| `API-R-02` | Contracts documented (OpenAPI) with contract tests in the integration suite | `core/09` §9.3 |
| `API-R-03` | AuthN on every non-public endpoint; AuthZ checked **server-side per operation** | `SEC-02` |
| `API-R-04` | Input validation at the boundary (schema validation), output encoding at rendering | `SEC-03`, `core/05` §5.3 |
| `API-R-05` | Parameterized queries / ORM bindings only | `SEC-03` |
| `API-R-06` | Error format decided and uniform (candidate: RFC 7807 Problem Details) | `IMP-05` |
| `API-R-07` | Every operation handles success, validation failure, server error, network error | `IMP-05` |
| `API-R-08` | Security headers, CORS allowlist, rate limiting, brute-force protection on auth surfaces | `SEC-07` |
| `API-R-09` | Every operation has a permissions-design row (roles, allowed actions, enforcement point) | `IMP-03` |
| `API-R-10` | Performance budgets measured per endpoint: reads p95 ≤ 500 ms, writes p95 ≤ 800 ms | `DOD-07` — `PROPOSED` targets, not confirmed for this project |
| `API-R-11` | Every implemented function has happy-path + validation-failure + authorization tests | `TST-02` |

## 6. Constraints

| Constraint | Status |
|---|---|
| Style/contract choices are `PROPOSED` until a Phase 02 ADR accepts them | `PROPOSED` |
| No endpoint may be written during Phase 00 (`SYS-01`) | `CONFIRMED` |
| Role set unknown → authorization matrix cannot be written | `BLOCKED` (`OQ-06`) |
| Error format not decided | `OPEN QUESTION` |
| Pagination/filtering/sorting conventions not decided | `OPEN QUESTION` |

## 7. Open questions

| ID | Question | Phase |
|---|---|---|
| `OQ-API-01` | Is REST+OpenAPI confirmed, or must alternatives (GraphQL, gRPC) be evaluated? | 02 |
| `OQ-API-02` | URL-based versioning (`/v1`) vs. header-based? | 02 |
| `OQ-API-03` | Error format: RFC 7807 or a custom envelope? | 02 |
| `OQ-API-04` | Pagination, filtering and sorting conventions? | 02 |
| `OQ-API-05` | Which endpoints are public vs. authenticated? | 01/02 |
| `OQ-API-06` | Is an API gateway/BFF in scope, or direct calls? (probably out of scope for coursework) | 02 |
| `OQ-API-07` | Are internal/event-driven contracts exposed via the same API surface? | 02 |

## 8. Validation needs (Phase 02 exit criteria for this document)

- [ ] OpenAPI document authored **before** implementation (API-first)
- [ ] Every `CONFIRMED` action from [`03-use-case-actions.md`](03-use-case-actions.md) maps to exactly one operation
- [ ] Every operation has an authorization decision + enforcement point (`API-R-09`)
- [ ] Error format and pagination conventions decided and recorded
- [ ] Performance budgets confirmed or explicitly marked `PROPOSED`
- [ ] Contract test suite planned (`13-testing-strategy.md`)
- [ ] Open questions `OQ-API-01`…`OQ-API-07` resolved or deferred with an owner
- [ ] Architecture review passed

## 9. Traceability references

- **Upstream:** [`03-use-case-actions.md`](03-use-case-actions.md) (actions) ·
  [`02-use-cases.md`](02-use-cases.md) · [`07-website-structure.md`](07-website-structure.md)
- **Downstream:** [`11-integration-specification.md`](11-integration-specification.md) (external contracts) ·
  [`12-security-specification.md`](12-security-specification.md) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) (contract tests) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 10. Related documents

- [`03-use-case-actions.md`](03-use-case-actions.md)
- [`11-integration-specification.md`](11-integration-specification.md)
- [`12-security-specification.md`](12-security-specification.md)
- [`../senior-rules/core/09_data_and_api.md`](../senior-rules/core/09_data_and_api.md)
