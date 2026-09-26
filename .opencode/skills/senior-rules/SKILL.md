---
name: senior-rules
description: Verification-layer skill wrapping the vendored senior-rules set (v2.0.0). Use to look up rule IDs and severities, run the validator, evaluate phase exit gates honestly, apply precedence (SEC > DOD > GEN-03 > IMP > DOC/AUD), and keep senior-rules/ unmodified. Load for any phase, any time.
---

# Skill — senior-rules (verification layer)

## Purpose

Be the checks, not the cheerleader: apply the rule set, run the validator, and report status
only as strong as the evidence behind it.

## When to load

Any phase, any time — especially before claiming `DONE`, before a commit, and at phase
closure.

## Core facts (`CONFIRMED`)

- Rules live in `senior-rules/` — **v`2.0.0`** per `senior-rules/VERSION` (root `CHANGELOG.md`
  records the upstream `2.1.0` discrepancy as finding `F-003`).
- Validator: `python senior-rules/validators/validate.py .` — on this Windows environment the
  command is `python`, **not** `python3`.
- Precedence (`GEN-07`): `SEC` > `DOD` > `GEN-03` > `IMP` > `DOC`/`AUD` > everything else.

## Standing obligations

1. **`senior-rules/` is read-only.** Never edit a rule or the validator to make a check pass
   (`ADP-03`, meta-rules §0.5). Never weaken a `CRITICAL` rule.
2. Every claim needs evidence; raw command output is pasted before any `DONE`
   (`GEN-04`, `DOD-10`).
3. A failing task is reported `INCOMPLETE` with the **failing gate named** — never averaged
   away.
4. A phase may not close with open `CRITICAL`/`HIGH` findings (`AUD-02`).
5. Findings follow the register format in root `Audit.md` (`AUD-01`), with rule ID, severity,
   evidence and status.

## Gate evaluation procedure

1. List the applicable gates (build · lint · tests · coverage · dead-element · security ·
   performance · docs · git).
2. Execute each; paste raw output as evidence.
3. Mark each `PASS` / `FAIL` / `BLOCKED` / `NOT APPLICABLE` — `NOT APPLICABLE` requires a
   reason and is **never** reported as `PASS`.
4. Overall status = the weakest honest result; report `INCOMPLETE` if any gate fails.

## Output contract

Gate table with evidence pointers, open-findings count by severity, status vocabulary
(`DONE` · `INCOMPLETE` · `BLOCKED` · `READY-FOR-REVIEW`).
