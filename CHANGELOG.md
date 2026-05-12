# Changelog

All notable changes to this scaffold will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Fixed

- `CLAUDE.md` — retracted false framework-inheritance claim that `LEARNING_LEDGER.md` contained _"78 entries, 11 themes."_ Audit on 2026-05-11 (in a JRF-update session) confirmed the file did not exist anywhere — public or private, local or remote, in any `jryan5150` or `Lexcom-Systems-Group-Inc` repo. The number was fabricated and shipped through v0.1 and v0.2.0 unchallenged. The file was then created with real seed entries (12 in v0.1, 20 in v0.3) and the row updated to reflect actual contents. The "scan its 11 recurring themes first" sentence in the bidirectional debt-ledger paragraph was similarly corrected to enumerate the actual themes and point at the ledger as the canonical list. **The retraction is preserved in the ledger's own v0.3 entry L009 (`Framework references must point at things that exist`)** so the corrective lesson outlives this CHANGELOG entry.

### Added

- `SECURITY.md` — security policy with private vulnerability reporting via
  GitHub Security Advisories. Honest framing of the thin attack surface
  for a markdown-only scaffold.
- `CONTRIBUTING.md` — explicit in-scope vs out-of-scope contribution guide.
  The "no philosophy" constraint is now load-bearing in PR review.
- `.github/workflows/docs.yml` — markdownlint + lychee link-check CI on
  every push and pull request. The "tests passing" pattern in prose-only
  repos.
- `.github/ISSUE_TEMPLATE/{bug,missing_example,identity_review}.md` —
  three structured issue surfaces. The Filled-IDENTITY-Review template
  invites public-IDENTITY conversations as a deliberate community feature.
- `.github/PULL_REQUEST_TEMPLATE.md` — checklist enforces scope constraints
  (no language opinions, no curated rule libraries, no Claude Code feature
  documentation belonging upstream).
- `.github/.markdownlint.json` — config tolerant of long lines, sibling
  duplicate headers in CHANGELOGs, and HTML in markdown (HTML-comment
  prompts are load-bearing UX in scaffolds).
- "Who this is for — and who it isn't" mini-section near the top of
  `README.md`. Lets users self-filter early without scrolling to the
  bottom-positioned "When NOT to adopt this scaffold" section.
- Cross-link from `README.md` to the [Four-Layer Context Architecture
  methodology page](https://github.com/jryan5150/portfolio/tree/main/methodologies/four-layer-context)
  in the related portfolio. The methodology page is the pattern-language
  version; this scaffold is the OSS-instance.
- `CLAUDE.md` updated with JRF Framework Inheritance block — references
  upstream `LEARNING_LEDGER.md` and the Pearl + Meadows NotebookLM
  foundational sources.

### Fixed

- The doc-vs-reality drift flagged in the 2026-05-02 OSS audit. README's
  _"Released: 2026-04-22 (v0.1 → v0.2.0)"_ claim now backed by an actual
  GitHub release tag (`v0.2.0`, retroactively cut against the original
  release commit).

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
