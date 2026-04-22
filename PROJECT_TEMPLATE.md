# CLAUDE.md — [Project Name]

> **Layer 4 of the harness.**
> Lives at the root of this project. Copy this template,
> rename to `CLAUDE.md`, fill in the sections.
> Delete sections you don't need — this is a skeleton, not a mandate.

---

## What This Is

<!--
  One paragraph. What does this project do? Who is it for?
  Write it so a collaborator (or future you) can understand the
  purpose in 30 seconds.
-->

---

## Stack

<!--
  Languages, frameworks, key dependencies, infrastructure.
  Just the facts — versions and names. No rationale here;
  rationale belongs in Architecture below if at all.
-->

- Language:
- Framework:
- Data layer:
- Infra / deploy:

---

## Commands

<!--
  The commands you run most often. Copy-paste-able.
  Don't document every command — just the ones that matter daily.
-->

- Install: `...`
- Dev server: `...`
- Test: `...`
- Lint / format: `...`
- Build: `...`
- Deploy: `...`

---

## Architecture

<!--
  2-3 paragraphs. Where does business logic live? Where does data live?
  What's the request flow? What are the bounded contexts?

  Keep it terse — the code is authoritative. This section exists
  so Claude knows where to look first, not so it can skip reading the code.
-->

---

## Conventions

<!--
  Project-specific patterns.
  Only things that differ from your global Layer 2 rules go here.
  If a convention is the same as your global style, don't repeat it —
  your Layer 2 rules already cover it.
-->

---

## Active Rules / Lenses

<!--
  Optional. Which of your Layer 1 / Layer 2 files matter most for this project?
  Useful when Claude needs to know which parts of your harness to emphasize.

  Example:
  - Rules: coding-style, testing, performance
  - Lenses: data-integrity, multi-tenancy
-->

---

## Known Gotchas

<!--
  Stuff that isn't obvious from the code.
  Historical context. Why you made non-obvious choices.
  Things that would trip up a new collaborator.

  This is one of the highest-value sections. Fill it ruthlessly.
-->

---

## Not In Scope

<!--
  The most valuable section of the template.
  What did you explicitly decide NOT to build? And why?

  Prevents scope creep, prevents Claude from volunteering features you rejected,
  and preserves context about trade-offs that would otherwise evaporate.

  Examples:
  - "No real-time updates — polling is good enough, WebSocket cost isn't worth it."
  - "No multi-tenancy — single-tenant by design, will never be multi."
  - "No admin UI — managed via CLI, UI would be a maintenance tax."
-->

---

## Status

<!--
  Current phase: active dev? Maintenance? Pre-launch? Production?
  Who's the user base right now?
  What's the next milestone?
-->

---

## Decision Log Pointer

<!--
  Optional. If this project has a structured decision log
  (architectural decisions, commercial choices, risk acceptances),
  point to it here.

  Example: "See `docs/decisions/` for ADRs."
-->
