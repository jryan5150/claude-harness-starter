# Changelog

All notable changes to this scaffold will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] — 2026-04-22

Major improvements responding to self-critique of v0.1.0. Focus: making
the first 15 minutes of adoption actually successful, and replacing
cop-outs with verified concrete documentation.

### Added

- `CLAUDE.md` at the repo root — the starter now dogfoods its own
  `PROJECT_TEMPLATE.md` as a worked example of a filled Layer 4 file.
- `IDENTITY.example.md` — fictional persona (Jordan Chen, senior web dev)
  demonstrating what a completed Layer 1 file looks like without imposing
  any specific philosophy on adopters.
- `rules/example-testing.md` — second worked rule example in a different
  domain, breaking the implicit assumption that rules must follow a single
  structure.
- `MIGRATION.md` — step-by-step guide for users with existing messy
  `~/.claude/` setups or giant per-project `CLAUDE.md` files.
- **Quick Start section** in `README.md` — a concrete 15-minute path to
  first value before committing to the full Identity layer effort.
- **ASCII cascade diagram** in `README.md` — visualizes how the layers
  flow and how memory operates orthogonally.
- **Opening pain hook** in `README.md` — sells the problem before the solution.
- **"When NOT to adopt this scaffold" section** in `README.md` — honest
  scope limits on who should and shouldn't use the framework.
- **"What I've Changed My Mind About" section** in `IDENTITY.md` — prompt
  that reveals thinking texture better than current convictions alone.
- **"Key Entrypoints" section** in `PROJECT_TEMPLATE.md` — tells Claude
  which 2-5 files to read first in a new project.
- **Concrete Claude Code loading instructions** in both `README.md` and
  `rules/README.md` — replaces the previous vague "check the current docs"
  cop-out with actual paths, precedence rules, and debugging commands.
- MIT license badge rendered at the top of `README.md`.

### Changed

- `PROJECT_TEMPLATE.md` — "Not In Scope" section moved to second position
  (right after "What This Is"). Context prevention beats context addition.
- `README.md` substantially restructured to lead with pain, then diagram,
  then quick-win path, then deeper bootstrap.

### Fixed

- Previous `rules/README.md` contained a cop-out ("check the current
  Claude Code docs, as the loading pattern has changed over versions").
  Replaced with verified concrete loading mechanism documentation
  (auto-discovery in `~/.claude/rules/`, `/memory` for debugging,
  `@` imports as optional explicit reference).

## [0.1.0] — 2026-04-22

Initial public release.

### Added

- Four-layer harness architecture explainer in `README.md`
  (Identity → Rules → Memory → Project).
- `IDENTITY.md` scaffold for Layer 1 — prompts for foundational axioms,
  patterns, design validation wall, and scope limits.
- `rules/README.md` explaining Layer 2 philosophy and when (not) to write rules.
- `rules/example.md` — worked example demonstrating the rule file pattern
  with generic git-workflow content.
- `memory/README.md` explaining Layer 3 (auto-managed) and types of memory
  worth keeping.
- `PROJECT_TEMPLATE.md` scaffold for Layer 4 per-project `CLAUDE.md` files.
- MIT license.
