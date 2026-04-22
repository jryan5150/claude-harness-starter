# Git Workflow (example rule file)

_Applies to: all dev work_

---

> **This is a worked example showing the rule file pattern.**
> It's intentionally generic — copy it, delete this note,
> rewrite the content to match how _you_ actually work.

---

## Commit Messages

- Imperative mood, max 72 character subject line.
- Body explains _why_, not _what_.
- Always include a co-author trailer if AI-assisted.

## Commit Scope

- One logical change per commit. Atomic.
- Separate refactors from feature additions.
- Separate formatting changes from behavior changes.

## Branch Naming

- `feature/description` — new functionality.
- `fix/description` — bug fixes.
- `chore/description` — maintenance, dependencies, config.
- Use kebab-case for the description.

## Protected Operations

- Never force-push to `main` or `master`.
- Never amend commits that have been pushed to a shared remote.
- Always pull before push.
- When pre-commit hooks fail, fix the issue and create a NEW commit —
  don't `--amend` to hide the failure.

## Sensitive Files

- Never commit `.env`, credentials, build artifacts, or large binaries.
- Verify `.gitignore` covers these before the first commit.
- Audit staged files before committing — catch accidental secrets.

---

## Notes on This Example

Notice what this file doesn't have:

- **No philosophy.** "Why imperative mood?" isn't explained. That's Layer 1 territory.
- **No tool specifics.** It doesn't say "use `git commit -m`" or reference any tooling.
- **No project detail.** It's global because these rules apply to every repo.
- **No long prose.** Short imperatives. Claude reads these fast and so do you.

If you find yourself wanting to explain _why_ a rule exists,
write it in your Layer 1 instead and reference it from Layer 2 by name.
