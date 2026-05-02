# Contributing to Claude Harness Starter

This is a deliberately minimal scaffold. Contributions that *narrow* the scope or *sharpen* the existing prompts are most welcome. Contributions that add language preferences, framework opinions, or curated rule libraries are usually rejected — the scaffold's value is that it ships **structure and prompts**, not philosophy.

If you're not sure whether a change fits, [open an issue first](https://github.com/jryan5150/claude-harness-starter/issues/new/choose). The discussion is cheap; un-merging an opinion-laden PR is expensive.

## What's in scope

- **Better prompts in scaffolds** — clearer, more pointed questions in `IDENTITY.md` and `PROJECT_TEMPLATE.md`. The HTML-comment prompts (`<!-- ... -->`) inside scaffolds are the load-bearing UX; improving them is the most valuable contribution path.
- **Better worked examples** — the existing examples (`IDENTITY.example.md` Jordan Chen persona, `rules/example.md` git workflow, `rules/example-testing.md` test discipline) deliberately ship in different domains to break the assumption of a single rule structure. Additional worked examples in *other* domains (frontend style, infra discipline, async patterns) are welcome — but they must be flagged as fictional and not impose opinions.
- **Migration guide improvements** — `MIGRATION.md` is the path most existing-mess users follow. Concrete decomposition examples (with redacted real-world inputs and outputs) help.
- **Loading-mechanism doc accuracy** — Claude Code's auto-discovery rules are upstream; if they change, the README's loading-instructions table needs to update. Verify against the latest [Claude Code docs](https://docs.claude.com/) and link the relevant page.
- **Linting / link-checking improvements** to the docs CI workflow.

## What's out of scope

- **Language or framework opinions.** Scaffolds are generic by design.
- **Tooling integration** (CI hooks, commit checks, editor plugins). Adopters add these per-project.
- **Curated rule libraries.** Two example rule files exist as format demonstrations; that's the limit. *Drop in a comprehensive testing-discipline rule library* belongs in a downstream fork, not this starter.
- **Claude Code feature deep-dives** (agents, commands, skills, MCP). Point users at upstream docs rather than duplicating them.

If a proposed change violates any of the above, it probably belongs in a downstream fork.

## Local setup

```bash
git clone https://github.com/jryan5150/claude-harness-starter.git
cd claude-harness-starter

# Optional: linting
npm install -g markdownlint-cli
brew install lychee  # link-checker; or `cargo install lychee`

# Lint
markdownlint --config .github/.markdownlint.json '**/*.md'
lychee --no-progress '**/*.md'
```

## PR conventions

- One change per PR — easier to review, easier to revert.
- Imperative-mood commit messages (`Add migration example`, not `Added migration example`).
- For AI-assisted commits, include `Co-Authored-By:` footer.
- If you change `README.md`, also update `CHANGELOG.md` under the `[Unreleased]` heading.
- If you change a scaffold file (`IDENTITY.md`, `PROJECT_TEMPLATE.md`, `rules/example*.md`), update the corresponding example or migration entry where applicable.

## License

By contributing, you agree your contributions are licensed under the [MIT License](LICENSE) of this project. No CLA required.

## Code of Conduct

Be civil. This is a small project maintained on the side; patience appreciated, and disagreements about scope are welcome — but they go in the issue thread, not the PR review.
