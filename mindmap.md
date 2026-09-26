# mindmap.md — Conceptual Hierarchy of the Traffic and Transport Management System

> **Read this as a map of *candidate* concepts, not a list of approved requirements.**
>
> Status labels used throughout: `CONFIRMED` · `PROPOSED DOMAIN` · `OPEN QUESTION` ·
> `ASSUMPTION` · `BLOCKED`. As of Phase 00, **no business requirement has been confirmed by
> any stakeholder**, so almost every node is `PROPOSED DOMAIN` or `OPEN QUESTION`.
>
> **Validator alias:** `mind_map.md` points here — see `Audit.md` finding F-001.
> Canonical file per project specification §7 is this file, `mindmap.md`.

---

## 0. Document control

| Field | Value |
|---|---|
| Status | `PROPOSED` concept inventory (Phase 00) |
| Phase | 00 — Initialization & Governance |
| Last updated | 2026-09-26 |
| Reviewed by | `OPEN QUESTION` — no stakeholder review yet |

---

## 1. Legend

| Label | Meaning |
|---|---|
| `CONFIRMED` | Verified by a stakeholder or by repository evidence. *(Currently: only project identity/objectives.)* |
| `PROPOSED DOMAIN` | A plausible domain boundary proposed by the architecture hypothesis. **Not** an approved requirement. |
| `OPEN QUESTION` | The concept exists but its meaning, scope, ownership or existence is unresolved. |
| `ASSUMPTION` | An unstated input we are provisionally assuming, pending validation. |
| `BLOCKED` | Cannot be progressed until an external input arrives. |

---

## 2. Root

```
Traffic and Transport Management System (TTMS)
├── Core Domain: Traffic Management
├── Supporting Domains
├── Actors & Users
├── Cross-Cutting Concerns
└── External Systems
```

---

## 3. Core domain

### 3.1 Traffic Management — `PROPOSED DOMAIN`

```
Traffic Management
├── Traffic Incidents .............. PROPOSED DOMAIN / OPEN QUESTION (vs. "Accidents")
├── Traffic Monitoring ............. PROPOSED DOMAIN
│   ├── Congestion ................. PROPOSED DOMAIN / OPEN QUESTION (measured how?)
│   ├── Sensor readings ............ OPEN QUESTION (is any real sensor available?)
│   └── Signal state observation ... PROPOSED DOMAIN
├── Traffic Signals ................ PROPOSED DOMAIN / OPEN QUESTION (control, or only monitor?)
├── Roads .......................... PROPOSED DOMAIN / OPEN QUESTION (own road model, or GIS-provided?)
└── Reports & Dashboards ........... PROPOSED DOMAIN (Phase 06)
```

**Open questions on the core domain**

| ID | Question |
|---|---|
| `MQ-01` | Is "Traffic Incident" distinct from "Accident", or are they the same concept under two names? |
| `MQ-02` | Does the system *control* traffic signals, or only *monitor/report* on them? |
| `MQ-03` | Is congestion derived from sensor data, from violations/incidents, or manually reported? |
| `MQ-04` | Does the system own a Road entity, or does it reference an external GIS/Mapping source? |

---

## 4. Supporting domains

Each is a `PROPOSED DOMAIN` unless annotated.

### 4.1 People & vehicles

```
Drivers ....................... PROPOSED DOMAIN / CONFIRMED as an actor concept only
├── Driver profile ............ PROPOSED DOMAIN
├── Citizen ................... OPEN QUESTION (is a Citizen distinct from a Driver?)
└── Driver record linkage ..... OPEN QUESTION (link to Civil Registry? see §7)

Vehicles ...................... PROPOSED DOMAIN
├── Vehicle profile ........... PROPOSED DOMAIN
└── Vehicle ownership ......... OPEN QUESTION (registration authority?)

Driving Licenses .............. PROPOSED DOMAIN
├── License issuance .......... OPEN QUESTION (who issues — this system or the Civil Registry?)
├── License classes ........... OPEN QUESTION (unknown set)
├── License expiry/renewal .... PROPOSED DOMAIN
└── Penalty points ............ PROPOSED DOMAIN / OPEN QUESTION (thresholds unknown)
```

### 4.2 Enforcement & liability

```
Violations .................... PROPOSED DOMAIN
├── Violation types ........... OPEN QUESTION (unknown catalogue — must NOT be invented)
├── Detection source .......... OPEN QUESTION (sensor? officer? camera? none confirmed)
└── Violation status lifecycle . OPEN QUESTION

Fines ........................ PROPOSED DOMAIN
├── Fine calculation .......... OPEN QUESTION (tariff source unknown)
├── Payment ................... PROPOSED DOMAIN / depends on Payment Gateway boundary
└── Payment status lifecycle .. OPEN QUESTION

Accidents ..................... PROPOSED DOMAIN
├── Accident report ........... PROPOSED DOMAIN
├── Parties involved .......... OPEN QUESTION
└── Emergency notification .... PROPOSED DOMAIN / depends on Police/Emergency boundary

Penalty Points ................ PROPOSED DOMAIN (cross-cutting between Violations & Licenses)
```

### 4.3 Output & delivery

```
Reports ....................... PROPOSED DOMAIN (Phase 06)
Notifications ................. PROPOSED DOMAIN / depends on Notification Provider boundary
├── Delivery channels ......... OPEN QUESTION (in-app? SMS? email? push?)
└── Recipient model ........... OPEN QUESTION
```

### 4.4 Platform / cross-cutting

```
Identity & Access ............. PROPOSED DOMAIN
├── Users ..................... PROPOSED DOMAIN
├── Roles ..................... PROPOSED DOMAIN / RBAC role set UNKNOWN (must not be invented)
├── Permissions ............... PROPOSED DOMAIN / enforcement point to be designed Phase 02
└── Authentication ............ PROPOSED DOMAIN (JWT, PROPOSED)

Audit ........................ PROPOSED DOMAIN
├── Audit trail ............... PROPOSED DOMAIN (see senior-rules LOG-01 relational log schema)
├── Audit findings ............ CONFIRMED — Audit.md exists and is in force
└── PII redaction ............. PROPOSED DOMAIN (senior-rules LOG-02)

Reports & Dashboards (UI) ..... PROPOSED DOMAIN (Phase 06)
```

---

## 5. Actors & users — `OPEN QUESTION`

Candidate actors only. **No actor has been confirmed by a stakeholder.**

| Candidate actor | Status | Notes |
|---|---|---|
| Citizen | `OPEN QUESTION` | Is this a user of the system, or a data subject? |
| Driver | `OPEN QUESTION` | Overlaps "Citizen"? |
| Traffic officer / police | `OPEN QUESTION` | Role in enforcement workflow unknown |
| System administrator | `PROPOSED` | Referenced by `senior-rules` templates (admin manages permissions) |
| Auditor | `PROPOSED` | Needed for the audit trail concept |
| Traffic controller / operator | `OPEN QUESTION` | Owns signals/monitoring? |
| Reporting analyst | `OPEN QUESTION` | Consumer of reports |
| External system (machine actor) | `PROPOSED` | See §7 |

**Candidate users** = the human instantiation of the actors above. None identified, no
personas created, no stakeholder names available. `OPEN QUESTION`.

---

## 6. Cross-cutting concepts

| Concept | Status | Notes |
|---|---|---|
| Requirements & traceability | `CONFIRMED` | Chain initialised in `docs/17-traceability-matrix.md` |
| Use cases & flows | `PROPOSED` | Skeleton in `docs/02-use-cases.md`, `docs/03-use-case-actions.md`, `docs/04-flow-actions.md`, `docs/05-flow-events.md` |
| Data flow | `PROPOSED` | Skeleton in `docs/06-data-flow.md` |
| Domain events | `PROPOSED` | Event catalogue not yet written — must not be invented |
| API surface | `PROPOSED` | `docs/10-api-specification.md` |
| Security (authN/authZ, validation, secrets) | `PROPOSED` | `docs/12-security-specification.md` |
| Quality attributes | `PROPOSED` | `docs/14-quality-attributes.md` |
| Risk | `CONFIRMED` (process) | `docs/15-risk-register.md` holds the register; entries are `PROPOSED` |
| Glossary | `PROPOSED` | `docs/16-glossary.md` |
| Sessions & recovery | `CONFIRMED` | `session_track.md` + `docs/sessions/` in force |
| Phases & gates | `CONFIRMED` | `development_phases_entry.md` |

---

## 7. External systems — each a `PROPOSED INTEGRATION BOUNDARY`

None confirmed. Existence, reachability, contract, protocol and ownership are all unknown.

| Candidate external system | Purpose (hypothesised) | Status |
|---|---|---|
| Civil Registry | verify citizen/driver identity; possibly license issuance | `PROPOSED INTEGRATION BOUNDARY` |
| Police / Emergency | accident & incident notification | `PROPOSED INTEGRATION BOUNDARY` |
| Payment Gateway | traffic fine payment | `PROPOSED INTEGRATION BOUNDARY` |
| Notification Provider | delivery of notifications | `PROPOSED INTEGRATION BOUNDARY` |
| GIS / Mapping | roads, locations, geocoding | `PROPOSED INTEGRATION BOUNDARY` |
| Traffic Sensor / Signal Simulator | sensor events, signal state | `PROPOSED INTEGRATION BOUNDARY` |

---

## 8. Explicitly NOT implied

The following are **not** asserted anywhere by this mind map:

- that every listed concept is an approved requirement
- that all listed concepts will be implemented
- that the listed external systems exist, are reachable, or are in scope
- any specific violation catalogue, fine tariff, penalty-point threshold, license class,
  role name, notification channel, or regulatory obligation — **none of these is known**
- any stakeholder, supervisor, citizen, officer or organisation name

## 9. Related documents

- [`architecture.md`](architecture.md) — architectural hypothesis and boundaries
- [`docs/01-requirements.md`](docs/01-requirements.md) — requirements foundation
- [`docs/02-use-cases.md`](docs/02-use-cases.md) — use-case skeleton
- [`docs/16-glossary.md`](docs/16-glossary.md) — terminology
- [`docs/17-traceability-matrix.md`](docs/17-traceability-matrix.md) — traceability chain
- [`memory.md`](memory.md) — cumulative project memory
