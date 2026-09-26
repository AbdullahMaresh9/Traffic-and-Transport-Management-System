# 07 — Website / Application Structure

| Field | Value |
|---|---|
| **Purpose** | Define the information architecture: pages, navigation, routes and the role-based views of the application. |
| **Scope** | Structural skeleton only. No screens are approved; no UI exists. |
| **Current Status** | Skeleton — **0 confirmed pages**; structure `PROPOSED`. |
| **Phase** | 00 foundation → designed in Phase 02, built in Phase 06 |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose

Give Phase 02 a stable place to record the application's structure and Phase 06 a structure
to build against, without asserting that any page is required today.

## 2. Scope

- **In:** route/page inventory (`PROPOSED`), navigation model, role-based visibility rules.
- **Out:** visual design, layout, components, interactions (→ [`08-ui-ux-specification.md`](08-ui-ux-specification.md)),
  and any implementation (Phase 06, gated by `SYS-01`).

## 3. Current status

| Metric | Value |
|---|---|
| Pages proposed | 14 |
| Pages confirmed | **0** |
| Roles that can view them | `OPEN QUESTION` — RBAC role set unknown (`OQ-06`) |
| UI code | none |

## 4. Known context

- Actors are unconfirmed ([`01-requirements.md`](01-requirements.md) §4), so any site map is
  provisional.
- `IMP-01`/`DOD-05` will require **every** rendered control to be wired to a real backend
  handler — an automated inventory test will diff this structure against the route registry
  in Phase 06.

## 5. Proposed site map (`PROPOSED`)

```
/                              Landing / overview            [PROPOSED]
├── /auth
│   ├── /login                                             [PROPOSED]
│   └── /register   ← OPEN QUESTION (self-registration?)   [OPEN QUESTION]
├── /drivers            Driver management                  [PROPOSED]
│   └── /drivers/:id
├── /vehicles           Vehicle management                 [PROPOSED]
│   └── /vehicles/:id
├── /licenses           License management                 [PROPOSED]
│   └── /licenses/:id
├── /violations         Violation management               [PROPOSED]
│   ├── /violations/:id
│   └── /violations/new  ← officer/admin only?             [OPEN QUESTION]
├── /fines              Fine & payment                     [PROPOSED]
│   └── /fines/:id
├── /accidents          Accident & incident reporting      [PROPOSED]
├── /monitoring         Congestion & signal monitoring     [PROPOSED]
├── /signals            Traffic signal state               [PROPOSED]
├── /reports            Reporting                          [PROPOSED]
├── /notifications      Notification inbox                 [PROPOSED]
├── /admin
│   ├── /admin/users    Users, roles, permissions          [PROPOSED]
│   └── /admin/audit    Audit trail viewer                 [PROPOSED]
└── /account            Own profile & settings             [PROPOSED]
```

## 6. Proposed navigation model

| Region | Contents | Visibility |
|---|---|---|
| Primary nav | Role-dependent links from §5 | `OPEN QUESTION` — depends on role set |
| Contextual actions | New/edit per view | each must be permission-gated **server-side** |
| Global | notifications, account, logout | `PROPOSED` |

**Rule (`CONFIRMED`):** hiding a nav item is *presentation only* — never counted as
authorization (`core/05` §5.2, IMP-03).

## 7. Confirmed information

The rule in §6 (UI hiding ≠ authorization) is `CONFIRMED`. **No page is confirmed.**

## 8. Assumptions

| ID | Assumption |
|---|---|
| `AS-W-01` | The deliverable is a responsive web application (single locale) |
| `AS-W-02` | Admin and auditor views are in scope |
| `AS-W-03` | Citizen self-service (login, view own fines) is in scope |

## 9. Open questions

| ID | Question |
|---|---|
| `OQ-W-01` | Which actor personas actually exist, and which pages do they need? (`OQ-11`) |
| `OQ-W-02` | Is there public (unauthenticated) content at all? |
| `OQ-W-03` | Must dashboards be role-specific? |
| `OQ-W-04` | Is a mobile/responsive requirement explicit, or desktop-only acceptable? |
| `OQ-W-05` | Is self-registration needed, or are accounts provisioned by an admin? |

## 10. Traceability references

- **Upstream:** [`01-requirements.md`](01-requirements.md) §4–§6 ·
  [`02-use-cases.md`](02-use-cases.md) (`UC-` → page mapping)
- **Downstream:** [`08-ui-ux-specification.md`](08-ui-ux-specification.md) ·
  [`10-api-specification.md`](10-api-specification.md) (each page → handlers) ·
  [`12-security-specification.md`](12-security-specification.md) (visibility rules) ·
  [`17-traceability-matrix.md`](17-traceability-matrix.md)

## 11. Related documents

- [`08-ui-ux-specification.md`](08-ui-ux-specification.md)
- [`01-requirements.md`](01-requirements.md)
- [`10-api-specification.md`](10-api-specification.md)
- [`../phases/phase-06-reporting-ui/PLAN.md`](phases/phase-06-reporting-ui/PLAN.md)
