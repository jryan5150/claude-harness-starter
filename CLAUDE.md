# CLAUDE.md — claude-harness-starter

> **What this is:** This IS the Claude Harness Starter repo itself —
> a minimal four-layer scaffold for setting up Claude Code as a solo developer.
>
> This file exists for two reasons:
>
> 1. When Claude Code is opened in this repo, it has Layer 4 context
>    for helping edit or evolve the scaffold.
> 2. It serves as a **worked example** of what a completed
>    `PROJECT_TEMPLATE.md` looks like when filled in.

---

## What This Is

A markdown-only scaffold that teaches a four-layer context architecture
for Claude Code. The scaffold is deliberately opinion-free — it ships
**structure and prompts**, not philosophy. Users write their own identity
layer, add their own rules as they earn them, and instantiate per-project
templates as they start new work.

---

## Not In Scope

The most important section for anyone editing this repo. We deliberately
do not ship:

- **Language or framework opinions.** Scaffolds are generic by design.
- **Tooling integration** (CI, hooks, commit checks). Users add their own.
- **Philosophy content.** The project ships the _shape_, not the _substance_.
- **Curated rule libraries.** We ship two example rule files as format
  demonstrations, nothing more.
- **Claude Code feature documentation.** Point users at the upstream docs
  rather than duplicating them.

If a proposed change violates any of the above, it probably belongs in
a downstream fork, not this starter.

---

## Stack

- Pure markdown. No build step. No dependencies. No toolchain.
- Consumed by humans first, Claude Code second.

---

## Commands

There is no toolchain. The project is read, copied, and modified by humans.

- Preview any file locally with any markdown viewer.
- Optional prose linting: `vale` or `markdownlint` if desired.
- Link checking: `lychee` or equivalent before releases.

---

## Architecture

Four layers, each represented by one or more files:

1. **Identity** — `IDENTITY.md` (scaffold) + `IDENTITY.example.md` (reference).
   The user's building philosophy.
2. **Rules** — `rules/` directory. Contains a README and two worked examples
   (`example.md` for git workflow, `example-testing.md` for test discipline).
3. **Memory** — `memory/README.md`. Documents the auto-memory layer.
   No installable content, just explanation.
4. **Project** — `PROJECT_TEMPLATE.md` (scaffold). Per-project instantiation.
   **This very file is a filled example of it.**

Supporting files:

- `README.md` — the main entry point, explains the 4-layer model.
- `MIGRATION.md` — guide for users with existing messy `~/.claude/` setups.
- `CHANGELOG.md` — version history, Keep-a-Changelog format.
- `LICENSE` — MIT.

---

## Key Entrypoints

- **New users:** `README.md` → `IDENTITY.example.md` → `PROJECT_TEMPLATE.md`.
- **Users with existing setups:** `README.md` → `MIGRATION.md`.
- **Users wanting a filled project example:** this file (`CLAUDE.md`).
- **Evolving the scaffold:** `CHANGELOG.md` + this file's "Not In Scope".

---

## Conventions

- **No imposed philosophy.** All scaffolds are empty prompts. Examples are
  explicitly fictional and flagged as such.
- **HTML comment prompts** (`<!-- ... -->`) inside scaffolds so users fill
  in content without leaving placeholder cruft after.
- **Line lengths under ~100** for readability in terminals and narrow panes.
- **No emoji in code/scaffolds.** Minor exceptions in README prose are fine.

---

## Known Gotchas

- `memory/` looks like a populated layer but only contains a README.
  That's intentional — memory is local and not shippable. First-time users
  occasionally expect files here.

- `IDENTITY.example.md` features a fictional persona named "Jordan Chen."
  Copying it wholesale defeats the purpose of the scaffold. The example
  is labeled with a warning at the top for exactly this reason.

- `rules/example.md` uses generic git-workflow content, which might lead
  users to think rule files must follow that specific structure. They don't.
  The second example (`rules/example-testing.md`) exists partly to break
  that assumption.

---

## Status

- **Phase:** Public scaffold, actively maintained.
- **Audience:** Solo developers and small teams setting up Claude Code.
- **License:** MIT — fully permissive, fork without attribution required.
- **Next milestone:** See `CHANGELOG.md` for version trajectory.

---

## Decision Log Pointer

No formal decision log for this repo yet. Material decisions are captured
in commit messages and `CHANGELOG.md`.
