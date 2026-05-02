# Claude Harness Starter

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A minimal scaffolding for setting up Claude Code as a solo developer.
This gives you the skeleton. You fill in the philosophy.

---

## The Problem This Solves

Ever notice you keep re-writing the same coding-style preferences in every
project's `CLAUDE.md`? That the corrections you gave Claude last week
resurface in a new session? That your hard-won opinions about testing,
git, and architecture live scattered across seven `CLAUDE.md` files and
none of them agree?

That's the "one giant CLAUDE.md per project" anti-pattern. It means every
new project re-derives your preferences from scratch, and your rules
never compound.

This scaffold fixes it by splitting your context across four layers.

### Who this is for — and who it isn't

**This scaffold is right for you if:**

- You work on **3+ active projects** and notice yourself re-typing the same preferences in each
- You've **corrected Claude on the same operational mistake twice** (the threshold for promoting a rule out of project-local memory)
- Your existing `CLAUDE.md` files have **drifted into mutual disagreement**
- You want **rules added today to benefit projects you haven't started yet**

**Skip this scaffold if:**

- You've **never corrected Claude.** Use Claude Code normally for a month first; you have nothing to put in Layer 1 or Layer 2 yet.
- You're a **one-project developer.** A single well-tended `CLAUDE.md` at that project's root beats this whole architecture.
- You're in a **team with established conventions.** Your personal Layer 1 and Layer 2 may conflict with team norms; the scaffold assumes you author your own harness.

The full *"When NOT to adopt this scaffold"* section is below for the deeper version.

---

## The Four Layers

```
    ┌─────────────────────┐
    │  1. IDENTITY.md     │   philosophy  —  rarely changes
    └──────────┬──────────┘
               │ constrains
    ┌──────────▼──────────┐
    │  2. rules/*.md      │   operating rules  —  occasional
    └──────────┬──────────┘
               │ constrains          ┌─────────────────────┐
    ┌──────────▼──────────┐          │  3. memory/         │
    │  4. project/CLAUDE  │◄─────────┤  accumulates across │
    └─────────────────────┘          │  all of the above   │
                                     └─────────────────────┘
```

| Layer           | What It Is                          | Where It Lives                      | How Often It Changes     |
| --------------- | ----------------------------------- | ----------------------------------- | ------------------------ |
| **1. Identity** | Your building philosophy            | `IDENTITY.md` (somewhere permanent) | Rarely — months to years |
| **2. Rules**    | How you operate day-to-day          | `~/.claude/rules/*.md`              | Occasionally             |
| **3. Memory**   | What Claude learned across sessions | `~/.claude/projects/.../memory/`    | Constantly, automatic    |
| **4. Project**  | Per-project specifics               | `<project>/CLAUDE.md`               | Per-project              |

**The cascade:** Layer 1 constrains Layer 2 constrains Layer 4.
Layer 3 accumulates orthogonally across all of them.

---

## Quick Start (15 minutes)

The fastest path to real value. Do this BEFORE you try to write your
full identity layer.

**1. Copy one rule file into Claude Code's global rules directory:**

```bash
mkdir -p ~/.claude/rules
cp rules/example.md ~/.claude/rules/git-workflow.md
```

Claude Code auto-discovers every `.md` file in `~/.claude/rules/` —
no configuration needed. Open any project in Claude Code and those
rules are now live.

**2. Copy the project template into an active project:**

```bash
cp PROJECT_TEMPLATE.md ~/projects/your-active-project/CLAUDE.md
```

Fill in the "What This Is" and "Not In Scope" sections first.
Everything else is optional at the start.

**3. Verify it worked:**

In a new Claude Code session inside that project, run `/memory` — you'll
see both your global rules and the project `CLAUDE.md` listed as loaded
context.

You now have a working two-layer setup. Return to Identity (Layer 1) and
the full bootstrap path below when you're ready.

---

## Full Bootstrap Path

### Step 1 — Rules (iterative, start here)

Copy `rules/example.md` and `rules/example-testing.md` into `~/.claude/rules/`.
Rename and rewrite them to match patterns you actually enforce.
Read `rules/README.md` for the full philosophy.

**Add new rules only after you've corrected Claude on the same thing twice.**
Premature rule-writing is the #1 failure mode here.

### Step 2 — Per-Project CLAUDE.md (immediate value)

For each active project, copy `PROJECT_TEMPLATE.md` to that project's root
as `CLAUDE.md`. Fill in what's specific to that project. Upper layers
handle everything else.

### Step 3 — Identity (slow)

Copy `IDENTITY.md` somewhere permanent. A folder like `~/projects/framework/`
or `~/.claude/IDENTITY.md` works. Keep it outside any single project —
it's not project-specific.

Reference `IDENTITY.example.md` for a fictional worked example showing
what a filled identity file looks like. Don't copy Jordan's content —
you want your own.

Sit with it. Fill in over weeks, not an afternoon. This is the slow-moving
layer — if you rush it, you'll end up writing aspirations instead of
convictions.

### Step 4 — Memory (automatic)

Read `memory/README.md`. You likely don't need to _do_ anything —
Claude Code auto-manages memory if you ask it to remember things.
Just know the pattern.

---

## How Claude Code Loads Your Context

Claude Code auto-discovers context from multiple locations, in this order
(later overrides earlier on conflict):

1. **User-level main file:** `~/.claude/CLAUDE.md`
2. **User-level rules:** `~/.claude/rules/*.md` (all files, recursive)
3. **Project ancestors:** `../CLAUDE.md`, `../../CLAUDE.md`, walking up
4. **Project root:** `./CLAUDE.md` or `./.claude/CLAUDE.md`
5. **Project local:** `./CLAUDE.local.md` (gitignored personal overrides)
6. **Project rules:** `./.claude/rules/*.md` (all files, recursive)

**No configuration needed.** Just put files in the right directories.

You can also import files explicitly with `@` syntax:

```markdown
@~/.claude/rules/coding-style.md
@docs/architecture.md
```

**Debug what's loaded:** In any Claude Code session, run `/memory` to see
every file Claude is reading and the load order.

**Exclude specific files** (useful in large monorepos): add to
`~/.claude/settings.json`:

```json
{
  "claudeMdExcludes": ["**/deprecated/CLAUDE.md"]
}
```

---

## Already Have a Messy `~/.claude/` Setup?

See **[`MIGRATION.md`](MIGRATION.md)** for a step-by-step decomposition of
existing giant `CLAUDE.md` files into the four-layer structure.

---

## Why This Pattern Works

- **No repetition.** Write "I always use named exports" once in Layer 2,
  not in every project's `CLAUDE.md`.
- **Fast project switching.** Each project's `CLAUDE.md` focuses on what's
  unique — not on re-establishing your preferences.
- **Compounding leverage.** Rules added today benefit projects next year.
  Your Layer 1 stabilizes over time and becomes a real asset.
- **Context-appropriate decisions.** Claude knows _which layer_ to consult.
  Architecture choice? Layer 1. Commit message? Layer 2. Which endpoint
  handles auth? Layer 4.

---

## The One Warning

**Don't write rules aspirationally.**

Every rule in Layer 2 loads into context on most sessions. That costs
tokens and mental overhead. A rule that applies to 5% of your work
is not a global rule — it belongs in a project's `CLAUDE.md`.

Curate ruthlessly. Five rules you religiously follow beats thirty rules
that are mostly ignored.

---

## When NOT to Adopt This Scaffold

- **You've never corrected Claude.** Without real data on what you'd tell
  Claude to do differently, you have nothing to put in Layer 1 or Layer 2
  yet. Use Claude Code normally for a month first.

- **You're a one-project developer.** This scaffold's value prop is
  _reuse across projects_. If you only work on one codebase, a single
  well-tended `CLAUDE.md` at its root beats this whole architecture.

- **You're in a team with established conventions.** Your personal
  Layer 1 and Layer 2 may conflict with team norms. The scaffold
  assumes you author your own harness.

---

## What's Not In This Starter

- **Actual philosophy.** Layer 1 is deliberately empty. You write it.
  A fictional example (`IDENTITY.example.md`) shows the shape.
- **Opinions on specific tools.** No language preferences, no stack
  opinions, no framework bias.
- **Claude Code feature deep-dives.** Agents, commands, skills, MCP —
  real and useful but beyond scaffold scope. Get the four layers working
  first, then layer in the advanced features.

---

## Maintenance

- **Quarterly:** Re-read Layer 1. Does it still reflect what you believe?
- **Monthly:** Audit Layer 2. Rules you never actually enforce? Delete them.
  Corrections you keep giving Claude that aren't in a rule yet? Add them.
- **Continuously:** Layer 3 maintains itself. Layer 4 lives with each project.

---

## Related / Upstream Docs

- **Claude Code docs** — the authoritative source for loading, memory,
  and settings. Search `docs.claude.com` for the current path.
- **[Four-Layer Context Architecture](https://github.com/jryan5150/portfolio/tree/main/methodologies/four-layer-context)** —
  the methodology page in [Jace Ryan's portfolio](https://github.com/jryan5150/portfolio)
  that describes the pattern in pattern-language form (when to use, when
  NOT to use, how it pairs with sister methodologies, foundational sources).
  This scaffold is the productized OSS-instance of that methodology.
- **[Keep a Changelog](https://keepachangelog.com/)** — format used by
  this repo's `CHANGELOG.md`.

---

## License

MIT. Fork freely. No attribution required, though appreciated.
