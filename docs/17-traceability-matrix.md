# 17 — Traceability Matrix

| Field | Value |
|---|---|
| **Purpose** | Maintain the end-to-end traceability chain so every confirmed requirement can be followed from origin through design to tests, and so missing coverage is detectable mechanically. |
| **Scope** | The chain definition, ID conventions, matrix structure and the current (empty) matrix. |
| **Current Status** | Structure initialized (`CONFIRMED`). **Matrix rows: 0** — no requirement is confirmed yet. |
| **Phase** | 00 (structure) → populated in Phase 01 and maintained continuously |
| **Last updated** | 2026-09-26 |

> Rule `SYS-05`: *every `CONFIRMED` major requirement must eventually be traceable through
> the full chain.* A requirement that cannot be traced is not ready for baseline.

---

## 1. The chain (`CONFIRMED`)

```
Requirement
  → User Story
    → Use Case
      → Business Rule
        → Domain Component
          → API
            → Database
              → Event
                → Integration
                  → Test Case
                    → Phase
```

## 2. ID conventions (`CONFIRMED`)

| Element | Format | Example | Notes |
|---|---|---|---|
| Requirement | `REQ-<NNN>` | `REQ-001` | assigned only when `CONFIRMED` |
| User story | `US-<NNN>` | `US-001` | INVEST criteria |
| Use case | `UC-<NN>` | `UC-08` | see [`02-use-cases.md`](02-use-cases.md) |
| Business rule | `BR-<CAT>-<NNN>` | `BR-AUTH-001` | from Source A `14` |
| Domain component | `DC-<name>` | `DC-Violation` | bounded-context element |
| API operation | `API-<res>-<verb>` | — | one per action in [`03-use-case-actions.md`](03-use-case-actions.md) |
| Database object | `DB-<table>` | — | see [`09-database.md`](09-database.md) |
| Event | `EV-<NN>` | `EV-09` | see [`05-flow-events.md`](05-flow-events.md) |
| Integration | `EXT-<NN>` | `EXT-03` | see [`11-integration-specification.md`](11-integration-specification.md) |
| Test case | `TC-<L>-<NNN>` | `TC-U-001` | `L` = U/C/I/S/UAT/P/Sec |
| Phase | `PH-<NN>` | `PH-01` | see [`../development_phases_entry.md`](../development_phases_entry.md) |
| Risk | `RISK-<NNN>` | `RISK-002` | see [`15-risk-register.md`](15-risk-register.md) |
| Finding | `F-<NNN>` | `F-005` | see [`../Audit.md`](../Audit.md) |
| ADR | `ADR-<NNNN>` | — | see [`decisions/`](decisions/) |

## 3. Matrix structure

One row per confirmed requirement; forward **and** backward traceability required.

| REQ | Title | Status | US | UC | BR | DC | API | DB | EV | EXT | TC | PH |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *— no rows yet —* | | | | | | | | | | | | |

**Backward check (essential):** every test case must point at a requirement. A test with no
upstream requirement is either a defect or a gold-plating signal (`05` QA: *"No gold
plating"*).

## 4. Current status

| Metric | Value |
|---|---|
| Requirements `CONFIRMED` | **0** |
| Matrix rows | **0** |
| Requirements `PROPOSED` (categories only) | 15 `FR-CAT` — see [`01-requirements.md`](01-requirements.md) §6 |
| Candidate use cases | 24 `PROPOSED` |
| Candidate events | 16 `PROPOSED` |
| Candidate integrations | 6 `PROPOSED INTEGRATION BOUNDARY` |
| Test cases | 0 |

> The chain structure exists; the chain is **empty**. This is the correct state at Phase 00 —
> populating it with invented rows would be fabrication.

## 5. Targets (`PROPOSED` rule defaults)

| Metric | Target | Source |
|---|---|---|
| Traceability completeness | **100%** of `CONFIRMED` requirements | Source A `14` metrics |
| Backward traceability | **100%** of test cases map to a requirement | `TST-02` spirit |
| Requirements volatility after baseline | **< 5%** churn | Source A `14` |
| Unresolved ambiguities at baseline | **0** | Phase 01 exit gate |

## 6. Traceability references

- **Upstream (chain roots):** [`00-project-charter.md`](00-project-charter.md) ·
  [`01-requirements.md`](01-requirements.md)
- **Chain carriers:** [`02-use-cases.md`](02-use-cases.md) ·
  [`03-use-case-actions.md`](03-use-case-actions.md) ·
  [`10-api-specification.md`](10-api-specification.md) ·
  [`09-database.md`](09-database.md) · [`05-flow-events.md`](05-flow-events.md) ·
  [`11-integration-specification.md`](11-integration-specification.md) ·
  [`13-testing-strategy.md`](13-testing-strategy.md) ·
  [`../development_phases_entry.md`](../development_phases_entry.md)
- **Gap detection inputs:** [`../Audit.md`](../Audit.md) (missing-work findings) ·
  [`15-risk-register.md`](15-risk-register.md)

## 7. Validation needs

- [ ] Every `CONFIRMED` requirement has a row before the Phase 01 gate
- [ ] No empty mandatory cell without an explicit `N/A` + reason
- [ ] Forward check: every requirement reaches at least one test case by Phase 07
- [ ] Backward check: every test case maps to a requirement
- [ ] Rows updated in the **same commit** as the artifact they reference (`DOC-05`)

## 8. Related documents

- [`01-requirements.md`](01-requirements.md)
- [`../development_phases_entry.md`](../development_phases_entry.md)
- [`13-testing-strategy.md`](13-testing-strategy.md)
- [`../Audit.md`](../Audit.md)
- [`16-glossary.md`](16-glossary.md)
