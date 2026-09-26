# 15 — Risk Register

| Field | Value |
|---|---|
| **Purpose** | Track everything that could prevent the project from meeting its objectives, with owners, scoring, response strategies and status. |
| **Scope** | Project + technical + process risks. Distinct from [`../Audit.md`](../Audit.md), which tracks **findings** (things already found wrong). |
| **Current Status** | Register active; **14 risks** entered. All `PROPOSED` (identified by analysis, not yet reviewed by a stakeholder). |
| **Phase** | 00 (created) → reviewed weekly once Phase 01 starts |
| **Last updated** | 2026-09-26 |

---

## 1. Purpose & method

Adopted from Source A `09` (ISO 31000-style), with one deliberate correction.

### Scoring

| Field | Scale |
|---|---|
| Probability (P) | 1 = very low … 5 = very high |
| Impact (I) | 1 = negligible … 5 = critical (project failure / safety / legal) |
| Risk score | `P × I` (1–25) |
| Risk level | **20–25 `CRITICAL` · 12–19 `HIGH` · 6–11 `MEDIUM` · 1–5 `LOW`** |

> **Correction recorded:** Source A's original bands (20–25 / 12–16 / 6–9 / 1–4) leave
> scores **10, 11, 17, 18, 19 unassigned**. This register uses the closed, exhaustive bands
> above so no score can fall through a gap. See `Audit.md` `F-011`.

### Response strategies

`AVOID` · `MITIGATE` · `TRANSFER` · `ACCEPT` · `ESCALATE`

### Fields per risk

`ID` · Description · P · I · Score · Level · Owner · Detection method · Mitigation ·
Contingency · Trigger · Status (`Active` / `Mitigated` / `Occurred` / `Closed`) · Last reviewed

## 2. The register

| ID | Risk | P | I | Score | Level | Owner | Mitigation | Trigger | Status |
|---|---|---|---|---|---|---|---|---|---|
| `RISK-001` | The required "PROJECT WHITEBOARD METHODOLOGY" appendix is never supplied, so Phase 00 cannot close cleanly. | 3 | 4 | **12** | `HIGH` | User | Obtain text; otherwise agree an explicit, documented alternative (`BLK-01`) | No response after next session | **Active** |
| `RISK-002` | No stakeholder/supervisor identified → requirements cannot be baselined, phases cannot be signed off. | 4 | 5 | **20** | `CRITICAL` | User | Identify supervisor and sign-off route before Phase 01 gate | Phase 01 gate arrives without an owner | **Active** |
| `RISK-003` | Requirement fabrication: plausible-but-invented requirements (violation catalogue, tariffs, roles) enter the baseline. | 3 | 5 | **15** | `HIGH` | AI + reviewer | `SYS-03`; every claim labelled; `OPEN QUESTION` instead of guessing | A document shows a specific tariff/threshold/role with no source | **Active** |
| `RISK-004` | External systems (6 candidate boundaries) do not exist or are unreachable → integration objective cannot be demonstrated. | 4 | 4 | **16** | `HIGH` | Requirements analyst | Confirm in Phase 01; fall back to simulators (`OQ-12`) before Phase 05 | Phase 01 closes with all 6 unconfirmed | **Active** |
| `RISK-005` | Scope is too large for the available time (15 functional categories, 24 use cases, 6 integrations). | 4 | 4 | **16** | `HIGH` | User + AI | MoSCoW prioritisation in Phase 01; explicit `Won't have` list | Phase 01/02 exceed their time boxes | **Active** |
| `RISK-006` | Phase 03 toolchain work is underestimated (CI, scanning, migrations, rollback rehearsal) → schedule slip. | 3 | 3 | **9** | `MEDIUM` | AI | Time-box; treat `F-012` as a scheduled deliverable | Phase 03 exceeds its plan | **Active** |
| `RISK-007` | Documentation drifts from implementation because updates are postponed. | 3 | 4 | **12** | `HIGH` | AI | `DOC-05` — docs updated in the same commit; validator as a drift check | A commit touches code without touching its docs | **Active** |
| `RISK-008` | AI overclaims completion ("DONE" without evidence) — the highest-consequence failure mode of AI-assisted development. | 3 | 5 | **15** | `HIGH` | AI + reviewer | `GEN-03`/`GEN-04`/`DOD-10`; raw output pasted before any claim; status vocabulary is closed | A report uses `DONE` with no attached output | **Active** |
| `RISK-009` | Upstream ADMR version ambiguity (`VERSION` 2.0.0 vs `CHANGELOG` 2.1.0) causes inconsistent rule enforcement. | 2 | 3 | **6** | `MEDIUM` | User | Resolve with upstream; pin explicitly in `RULES_HINTS.md` §1 | Rules cited inconsistently between sessions | **Active** |
| `RISK-010` | `python3` vs `python` environment mismatch breaks the mandated validator command for future sessions. | 2 | 3 | **6** | `MEDIUM` | AI | Already documented in `RULES_HINTS.md` §3 and `CF-03` | A session reports the validator as "not found" | **Mitigated** |
| `RISK-011` | No CI/branch protection/secret scanner (`F-012`) → security and DOD gates are unenforceable. | 3 | 4 | **12** | `HIGH` | AI | Scheduled into Phase 03 as an explicit deliverable | Phase 03 gate arrives with scanning still absent | **Active** |
| `RISK-012` | Ambiguous requirements (incident vs. accident, signal control vs. monitor) produce contradictory designs. | 4 | 3 | **12** | `HIGH` | Requirements analyst | Resolve all `MQ-*`/`OQ-*` in Phase 01 before Phase 02 starts | Two documents describe the same concept differently | **Active** |
| `RISK-013` | Over-engineering: adopting enterprise patterns (service meshes, multi-region DR, policy engines) beyond academic need. | 3 | 3 | **9** | `MEDIUM` | AI + reviewer | Explicit `NOT APPLICABLE` decisions with reasons; favour clarity over complexity | An ADR introduces infrastructure with no demonstrable learning value | **Active** |
| `RISK-014` | Weak sign-off culture: AI-simulated personas or invented "reviewer approvals" presented as real verification. | 2 | 5 | **10** | `MEDIUM` | AI + user | Every claimed sign-off needs a file path + evidence reference; simulated data never reported as real research | A document states "approved by" with no artifact | **Active** |

## 3. Risk summary

| Level | Count | IDs |
|---|---|---|
| `CRITICAL` (20–25) | 1 | `RISK-002` |
| `HIGH` (12–19) | 8 | `RISK-001`, `RISK-003`…`RISK-005`, `RISK-007`, `RISK-008`, `RISK-011`, `RISK-012` |
| `MEDIUM` (6–11) | 5 | `RISK-006`, `RISK-009`, `RISK-010`, `RISK-013`, `RISK-014` |
| `LOW` (1–5) | 0 | — |

**Top risk:** `RISK-002` (no identified stakeholder) — it blocks both the Phase 01 and
Phase 02 gates, so it must be resolved first.

## 4. Assumption analysis (per Source A `09`)

Every assumption in the project must be challengeable with *"What if this assumption is
wrong?"* and must be validated with the stakeholder and tracked as validated/unvalidated.
Current assumption registers: [`../memory.md`](../memory.md) `Assumptions` ·
[`01-requirements.md`](01-requirements.md) §9 · per-document `Assumptions` sections.

**No assumption has been validated yet** — there is no stakeholder to validate against (`RISK-002`).

## 5. Review cadence

| When | Action |
|---|---|
| Weekly during active phases | review all `Active` risks; update P/I, status, last-reviewed |
| At every phase gate | re-score; no `CRITICAL` risk may be unowned at a gate |
| On any new finding in `Audit.md` | check whether it implies a new risk |

## 6. Traceability references

- **Upstream:** [`../Audit.md`](../Audit.md) (findings → risks) ·
  [`00-project-charter.md`](00-project-charter.md) §4 (assumptions) ·
  [`01-requirements.md`](01-requirements.md) §10 (open questions)
- **Downstream:** [`../phases/phase-01-analysis/PLAN.md`](phases/phase-01-analysis/PLAN.md) §risks ·
  [`../phases/phase-02-architecture/PLAN.md`](phases/phase-02-architecture/PLAN.md) §risks ·
  [`14-quality-attributes.md`](14-quality-attributes.md) (unquantified targets)

## 7. Related documents

- [`../Audit.md`](../Audit.md) — findings register (complementary, not duplicate)
- [`14-quality-attributes.md`](14-quality-attributes.md)
- [`../senior-rules/core/00_meta_rules.md`](../senior-rules/core/00_meta_rules.md)
