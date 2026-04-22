# Migration Guide

For users with an existing messy `~/.claude/` setup or giant per-project
`CLAUDE.md` files who want to decompose into the four-layer structure.

---

## Who This Is For

- You've been using Claude Code for a while.
- You have `CLAUDE.md` files in several projects that each grew to 300+ lines.
- You notice the same preferences show up in every one of those files.
- Your `~/.claude/CLAUDE.md` (if it exists) is either empty or a dumping ground.

If you're new to Claude Code, skip this file. Read `README.md` and start
fresh with the Quick Start.

---

## Before You Start

Spend 30 minutes inventorying what you have:

1. **List every `CLAUDE.md` you've written:**

   ```bash
   find ~ -name "CLAUDE.md" -not -path "*/node_modules/*" 2>/dev/null
   ```

2. **Print them side-by-side** if you can. Physical paper helps.

3. **Mark each line** with a label:
   - **P** — philosophy ("why I build things this way")
   - **R** — rule ("how I always do X")
   - **J** — project-specific ("this project has Y")
   - **D** — duplicate ("this appears in another CLAUDE.md too")

You now have the raw material for the decomposition.

---

## The Decomposition

### Step 1 — Extract Rules (R and D lines)

Anything marked **R** that appears in more than one `CLAUDE.md` is a
**Layer 2 rule**.

Create `~/.claude/rules/<topic>.md` files. Start with obvious groupings:

- `coding-style.md` — naming, formatting, imports, function length.
- `git-workflow.md` — commit conventions, branch names, PR patterns.
- `testing.md` — coverage rules, mocking discipline, test structure.
- `security.md` — secrets management, input validation, auth patterns.

For each new rule file:

- Pull the relevant lines out of every project `CLAUDE.md` where they appeared.
- Consolidate duplicates into one canonical statement.
- **Delete the originals from each project `CLAUDE.md`.**
  (This is the hard part. Do it anyway.)

### Step 2 — Extract Identity (P lines)

Anything marked **P** — "I prefer domain-driven design," "I design for
failure," "I hate heavy ORMs" — is **Layer 1 identity**, not a rule.

Create `IDENTITY.md` somewhere permanent (e.g., `~/.claude/IDENTITY.md`
or `~/projects/framework/IDENTITY.md`). Move the philosophy lines there.

Consult `IDENTITY.example.md` in the starter for section structure.
Don't worry about filling every section — some philosophy emerges slowly.

### Step 3 — Slim Each Project CLAUDE.md

After Steps 1 and 2, every project `CLAUDE.md` should contain ONLY:

- What the project is and who it's for.
- What's deliberately NOT in scope.
- Stack.
- Commands.
- Key entrypoints.
- Architecture notes.
- Project-specific conventions (things that _override_ your global rules).
- Known gotchas.
- Status.

Use `PROJECT_TEMPLATE.md` from the starter as a guide.

Most project `CLAUDE.md` files shrink by 60–80% in this step. That's
the whole point — the information didn't disappear, it moved to layers
where it belongs and compounds.

### Step 4 — Verify Loading

Open each project in Claude Code and run `/memory`. You should see:

- User-level files (`~/.claude/CLAUDE.md` if present, plus your rules).
- The project `CLAUDE.md`.
- Any ancestor `CLAUDE.md` files (like `~/projects/CLAUDE.md` for
  workspace-wide rules).

If something you expected isn't listed, check:

- File is named exactly `CLAUDE.md` (case matters on Linux).
- Rule files end in `.md` and live under `~/.claude/rules/` or a subdirectory.
- No `claudeMdExcludes` in `settings.json` is filtering it out.

---

## Worked Example (Before and After)

### Before — one project's CLAUDE.md (340 lines)

```markdown
# My SaaS Project

## Coding Style

- Use TypeScript, prefer named exports, use Zod for validation...
  [60 lines]

## Git

- Commits should be imperative, under 72 chars, include co-author trailer...
  [25 lines]

## Testing

- 80% coverage minimum, integration tests for critical paths...
  [40 lines]

## Architecture

- Express + Drizzle, handlers in routes/, logic in domain/...
  [30 lines]

## Why we chose Postgres

- We considered Mongo but the relational schema wins because...
  [15 lines — this is philosophy disguised as project doc]

## Known Issues

- The webhook handler retries 3x on 5xx but we haven't confirmed...
  [20 lines]

[... 150 more lines of mixed philosophy, rules, and project detail]
```

### After — three files

**`~/.claude/rules/coding-style.md`** (new, ~30 lines)
Everything TypeScript / Zod / naming that applies to all projects.

**`~/.claude/rules/git-workflow.md`** (new, ~20 lines)
Commit conventions shared across all projects.

**`~/.claude/rules/testing.md`** (new, ~25 lines)
Coverage, mocking, integration-test rules for all projects.

**`~/IDENTITY.md`** (new, grows over time)
"Why we chose Postgres" becomes the axiom "relational-first, document
store only when justified by access pattern."

**`~/projects/my-saas/CLAUDE.md`** (slimmed, ~80 lines)

```markdown
# My SaaS Project

## What This Is

B2B invoicing SaaS for freelancers. ~500 users, $10k MRR.

## Not In Scope

- No multi-tenancy. Single-tenant by design.
- No real-time updates. Polling is fine at our scale.

## Stack

- Node 20, TypeScript, Express, Drizzle, Postgres.

## Commands

- `pnpm dev`, `pnpm test`, `pnpm migrate`, `pnpm deploy`

## Key Entrypoints

- `src/server.ts` — bootstrap.
- `src/routes/` — HTTP handlers, thin glue.
- `src/domain/` — business logic, pure functions.

## Architecture

[2 paragraphs]

## Known Gotchas

- Stripe webhook retries: [specifics].
- Session expiry edge case: [specifics].

## Status

Production. 500 users. Next milestone: team plan rollout Q2.
```

Total content is roughly the same. But now the rules benefit every
future project, the identity is permanent, and this file is focused
on _this project_.

---

## Common Pitfalls

1. **Copying the same rule into multiple layers "just in case."**
   Don't. If it's in Layer 2, remove it from Layer 4. Duplication in
   context wastes tokens and creates conflict-resolution ambiguity.

2. **Writing aspirational rules during migration.**
   Only migrate things you've actually been enforcing. Migration is
   an audit, not a redesign.

3. **Trying to fill `IDENTITY.md` completely in one sitting.**
   Start with 2–3 axioms you're sure of. Leave the rest empty.
   Identity accrues over weeks.

4. **Deleting project context that looks "general but actually isn't."**
   "We chose Postgres" might read like a rule, but the _reason_ is
   project-specific. Move the general preference for relational databases
   to identity; keep the project-specific justification in project docs.

5. **Skipping the `/memory` verification step.**
   Assuming files are loaded when they aren't is the #1 reason migration
   appears to fail. Always verify.

---

## After Migration

Give the new structure 2 weeks before judging. The benefit compounds
slowly: every time you start a new project and realize you didn't need
to re-derive your style preferences, that's the system paying off.

If something feels wrong — a rule that doesn't fit a project, a line
that keeps wanting to move between layers — trust that signal. The
layer boundaries aren't perfect, and your own version will have its
own edge cases.
