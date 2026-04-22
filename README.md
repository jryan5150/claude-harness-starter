# Claude Harness Starter

A minimal scaffolding for setting up Claude Code as a solo developer.
This gives you the skeleton. You fill in the philosophy.

---

## The Idea

Claude Code works better when it has layered context. Most people stuff
everything into a single `CLAUDE.md` in each project and end up re-deriving
the same preferences, rules, and patterns for every new repo.

This scaffold splits your context across four layers so that stable things
stay stable and volatile things stay volatile. The payoff: new projects
bootstrap faster, your rules compound over time, and Claude has the right
context for the right decision.

---

## The Four Layers

| Layer           | What It Is                                         | Where It Lives                      | How Often It Changes         |
| --------------- | -------------------------------------------------- | ----------------------------------- | ---------------------------- |
| **1. Identity** | Your building philosophy, axioms, what you believe | `IDENTITY.md` (somewhere permanent) | Rarely — months to years     |
| **2. Rules**    | How you operate day-to-day                         | `~/.claude/rules/*.md`              | Occasionally                 |
| **3. Memory**   | What Claude has learned across your sessions       | `~/.claude/projects/.../memory/`    | Constantly, mostly automatic |
| **4. Project**  | Per-project specifics                              | `<project>/CLAUDE.md`               | Every project                |

The cascade: **Layer 1 constrains Layer 2 constrains Layer 4.**
**Layer 3 accumulates observations across all of them.**

Think of it like a pyramid. The top is hard to change but rarely needs to.
The bottom changes constantly but inherits stability from above.

---

## How to Bootstrap (in order)

### Step 1 — Identity (slow)

Copy `IDENTITY.md` somewhere permanent. A folder like `~/projects/framework/`
or `~/.config/dev-framework/` works. Keep it outside any single project
because it's not project-specific.

Sit with it. Fill it in over weeks, not an afternoon. This is the slow-moving
layer — if you rush it, you'll end up writing aspirations instead of convictions.

### Step 2 — Rules (iterative)

Copy `rules/example.md` into `~/.claude/rules/` as a template.
Start with 2–3 rules you know you apply to everything (coding style,
git workflow, testing). Read `rules/README.md` for the full philosophy.

**Add new rules only after you've corrected Claude on the same thing twice.**
Premature rule-writing is the #1 failure mode here.

### Step 3 — Memory (mostly automatic)

Read `memory/README.md` and understand what's there. You probably don't
need to _do_ anything — Claude Code auto-manages this if you ask it
to remember things. Just know the pattern.

### Step 4 — Project (per-project)

For each project, copy `PROJECT_TEMPLATE.md` to that project's root
as `CLAUDE.md`. Fill in what's specific to that project and let the
upper layers handle the rest.

---

## Why This Pattern Works

- **No repetition.** Write "I always use named exports" once in Layer 2,
  not in every project's `CLAUDE.md`.
- **Fast project switching.** Each project's `CLAUDE.md` focuses on what's
  unique — not re-establishing your preferences.
- **Compounding leverage.** Rules added today benefit projects next year.
  Your Layer 1 stabilizes over time and becomes a real asset.
- **Context-appropriate decisions.** Claude knows _which layer_ to consult.
  Architecture choice? Layer 1. Commit message? Layer 2. Which endpoint
  handles auth? Layer 4.

---

## The One Warning

**Don't write rules aspirationally.**

Every rule in Layer 2 gets loaded into context on most sessions. That costs
tokens and mental overhead. A rule that only applies to 5% of your work
is not a global rule — it belongs in the relevant project's `CLAUDE.md`.

Curate ruthlessly. It's better to have 5 rules you religiously follow
than 30 rules that are mostly ignored.

---

## What's Not In This Starter

- **Actual philosophy.** Layer 1 is deliberately empty. You write it.
- **An opinion on specific tools.** No language preferences, no stack
  opinions, no framework bias. Those are Layer 2 concerns and yours to define.
- **Agents, commands, skills.** Claude Code supports these, but they're
  beyond the scope of markdown setup. Get the four layers working first.

---

## Maintenance

- **Quarterly:** Re-read Layer 1. Does it still reflect what you believe?
- **Monthly:** Audit Layer 2. Any rules you never actually follow? Delete them.
  Any corrections you keep giving Claude that aren't in a rule yet? Add them.
- **Continuously:** Layer 3 maintains itself. Layer 4 lives with each project.

That's it. Good luck.
