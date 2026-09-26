---
name: parallel-execution
description: Parallel work orchestration skill for TTMS. Use when splitting a phase scope into independent units, running subagents or parallel tool calls safely, avoiding write conflicts on shared docs, and merging results with evidence. Load for Phase 03+ implementation work or any large documentation batch.
---

# Skill — parallel-execution

## Purpose

Increase throughput without losing auditability: independent units run in parallel, shared
documents stay consistent, and every unit still carries its own evidence.

## When to load

- Phase 03+ work with independent slices; large documentation batches; multi-agent sessions.

## Splitting rules

1. Split **only** by independence: two units are parallel-safe iff they touch disjoint files
   or one is read-only for the other.
2. Shared canonical files (`ENTRY.md`, `memory.md`, `Audit.md`, `session_track.md`,
   phase `TODO.md`/`AUDIT.md`, `CHANGELOG.md`) are **serial-only** — merge them on the main
   thread, never from two workers.
3. Each unit gets: its scope, the rules that apply (`RULES_HINTS.md` excerpt), the exact
   files it may touch, and its evidence obligation (`GEN-04`).
4. One session executes **one** phase scope overall; parallelism subdivides that scope, it
   does not widen it (`SYS-01` scope fence still applies).

## Merge rules

1. Workers return: files touched, raw gate output, findings, status — no free prose claims.
2. Main thread reconciles: deduplicate findings into `Audit.md`, update `TODO.md` once,
   re-run `python senior-rules/validators/validate.py .` after the merge.
3. If two units conflict on content, the conflict is resolved by the **rule** with higher
   precedence (`SEC` > `DOD` > `GEN-03` > `IMP` > `DOC`/`AUD`), not by preference.

## Failure handling

- A worker that cannot produce evidence returns `BLOCKED` with the reason — the main thread
  reports the scope `INCOMPLETE`, naming the failing unit/gate (`DOD-10`).
- Never let a parallel result be committed without the merged validator run (`VCS-04`).

## Output contract

Unit table (unit × files × status × evidence pointer) + merged validator output +
Done / Remaining / Next.
