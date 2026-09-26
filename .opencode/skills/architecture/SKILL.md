---
name: architecture
description: Architecture skill for TTMS. Use for system context and boundaries, component decomposition, integration patterns (sync/async), data architecture outlines, ADR writing, and architecture reviews against quality attributes. Advisory until Phase 02 gate passes.
---

# Skill — architecture

## Purpose

Structure architectural thinking so decisions are traceable to quality attributes and
requirements — not to habit or fashion.

## When to load

Phase 02 and Phase 03 primarily; any change to components, boundaries, data stores or
integrations later on.

## Procedure

1. **Context first:** system boundaries, actors, external systems (confirmed vs `PROPOSED`).
2. **Quality-attribute driven:** read `docs/14-quality-attributes.md`; each significant
   decision names the attribute(s) it serves and the trade-off it accepts.
3. **Decompose:** components with single responsibility, explicit interfaces, explicit data
   ownership. No component exists without a requirement behind it.
4. **Integration model:** cover both synchronous and asynchronous flows as required, with
   correlation, timeout, retry and failure semantics designed up front.
5. **Data architecture outline:** what data exists, ownership, consistency needs — the
   physical schema is Phase 03 work.
6. **Security architecture:** trust boundaries, authorization model, secrets handling
   (`SEC-*` precedence over everything else).
7. **Record decisions:** one ADR per significant choice
   (`docs/decisions/TEMPLATE_adr.md`) — context, options, decision, consequences.
8. **Review:** trace requirements ↔ architecture both directions; untraced requirement or
   unforced decision = finding.

## Hard limits

- No application code before Phase 01 **and** Phase 02 gates `PASS` (`SYS-08`).
- No invented external systems, APIs or regulations (`SYS-03`) — label `PROPOSED`.
- Keep `architecture.md` §7 delta log current in the same commit (`DOC-05`).

## Output contract

Decisions as ADR-linked tables with quality attributes, alternatives and consequences; status
labels on every claim; Done / Remaining / Next.
