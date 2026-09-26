---
name: traffic-domain
description: Traffic and transport domain skill for TTMS. Use for domain concept discussions (driver, vehicle, license, violation, fine, accident, incident, road, junction, patrol, traffic signal), bounded contexts, terminology from the glossary and mindmap, and domain-accurate wording in requirements or design. Documentation-only until Phase 01/02 gates PASS.
---

# Skill — traffic-domain (traffic & transport management domain)

## Purpose

Keep the language of the project precise and consistent: one concept, one name, one meaning —
so requirements, design, database and tests can be traced to each other.

## When to load

- Phase 01 domain/concept analysis and glossary work.
- Any discussion of driver / vehicle / license / violation / fine / accident / incident /
  road / junction / patrol / signal concepts in requirements, design or data modeling.

## Canonical sources (`CONFIRMED`)

- `mindmap.md` — conceptual hierarchy with status labels (root canonical).
- `docs/16-glossary.md` — term definitions.
- `docs/01-requirements.md` — problem context and requirement catalogue.

## Working rules

1. **Define before use.** A term not in the glossary gets added there first, then used.
2. **Distinguish carefully:** violation vs. fine (offence vs. monetary consequence) ·
   accident vs. incident (harm event vs. generic event) · license status vs. license class ·
   vehicle ownership vs. vehicle operation.
3. **Respect the scope fence:** domain *concepts* may be analysed and documented in Phase 01;
   domain *workflows* (CRUD, APIs, dashboards) may not be implemented until Phase 01 **and**
   Phase 02 gates `PASS` (`SYS-01`, `SYS-08`).
4. **No invention:** jurisdiction-specific regulations, authority names, fine amounts or
   penalty scales are `OPEN QUESTION` until supplied by a real source (`SYS-03`). Never cite
   a law that was not provided.
5. Actors and roles (driver, officer, inspector, administrator, …) are `PROPOSED` candidates
   until stakeholder confirmation (`F-006`).

## Output contract

Domain tables: term · definition · status label · source · related requirements. Any
unconfirmed domain fact ends as `OPEN QUESTION`, never as a statement.
