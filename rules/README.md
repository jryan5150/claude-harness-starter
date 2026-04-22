# Rules — Layer 2 of the Harness

This is how you operate day-to-day. Short, actionable, load-bearing.

---

## Where These Go

Copy individual rule files into **`~/.claude/rules/`**.

**Claude Code auto-discovers every `.md` file in that directory** at the
start of every session — no configuration needed. Subdirectories are
searched recursively, so you can organize by concern:
`~/.claude/rules/frontend/`, `~/.claude/rules/backend/`, etc.

**No reference from `~/.claude/CLAUDE.md` is required.** Discovery is automatic.

### Project-scoped rules

Same pattern works for project-specific rules: put them in
`<project>/.claude/rules/*.md`. Project rules load after user-global
rules, so project rules win on conflict.

### Debugging

In any Claude Code session, run `/memory` to see every file that's
currently loaded, in order. If a rule file isn't listed, it isn't
being loaded — check the filename (must end in `.md`) and path.

### Optional: `@` imports

If you want to reference a rule explicitly from a CLAUDE.md rather than
rely on auto-discovery, use `@`-import syntax:

```markdown
@~/.claude/rules/coding-style.md
@docs/architecture.md
```

Useful when you want a specific load order or when your rule lives
outside the standard directories.

---

## When to Write a Rule

**Only after you've corrected Claude on the same thing twice.**

This is the single most important discipline in Layer 2.

Rules loaded into every session cost context tokens and mental overhead.
If a rule applies to less than half your work, it probably belongs in a
project `CLAUDE.md` (Layer 4), not here.

### Good triggers for a new rule

- You've given the same correction in 3+ sessions.
- You notice a pattern in bugs or PRs you could have prevented with a standing rule.
- You made an architectural choice you want to be the default going forward.

### Bad triggers for a new rule

- "This seems like a good idea."
- "I read about this best practice."
- "This might be useful someday."

---

## File Naming

Use kebab-case, descriptive names that name the _concern_, not the tool:

**Good:**

- `coding-style.md`
- `git-workflow.md`
- `testing.md`
- `security.md`
- `performance.md`

**Less good (too specific, too tool-bound):**

- `eslint-config.md` — tools change, write about style instead
- `jest-patterns.md` — same
- `aws-deployment.md` — same

Most solo devs start with 4–6 rules total and stay under 15 long-term.
If you have 20+ rule files, you're probably using this layer for things
that belong in Layer 1 or Layer 4.

---

## Structure of a Rule File

See `example.md` in this directory for a worked example.

Each rule file should have:

1. **A scope header** — `*Applies to: X*` so you (and Claude) know when it's active.
2. **Short, actionable statements** — imperative, concrete.
3. **Optional small examples** — only when the pattern is non-obvious.
4. **No theory, no philosophy** — that's Layer 1 (`IDENTITY.md`).
5. **No project-specific detail** — that's Layer 4 (`CLAUDE.md`).

Rules are operational. They tell Claude what to do, not why.
The "why" lives in your Layer 1 and occasionally in PR descriptions.

---

## What Rules Are NOT

- **Documentation** — write this in project READMEs instead.
- **Philosophy** — that's Layer 1.
- **Onboarding** — that's a project README.
- **TODO lists** — that's a task tracker.

If a rule file is growing past ~200 lines, it's probably two concerns merged.
Split it.

---

## Maintenance

Audit your rules monthly:

- **Which rules have I actually enforced in the last 30 days?**
  If the answer is zero, consider deleting or merging.
- **What corrections have I given Claude repeatedly that aren't in a rule yet?**
  Add those.
- **Has my Layer 1 shifted in a way that invalidates any of these rules?**
  Update or remove the now-inconsistent ones.

Deleting rules is as important as writing them. An unenforced rule
trains you to ignore the rules that matter.
