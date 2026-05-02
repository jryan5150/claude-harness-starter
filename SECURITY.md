# Security Policy

This is a markdown-only scaffold — no executable code, no runtime, no network surface. The security profile is correspondingly thin. The threats this scaffold could plausibly enable:

1. **Adopters embedding secrets in `IDENTITY.md` or rule files** that then get committed publicly. This is a process problem, not a code problem; the scaffold's docs flag it (see [README — "The One Warning"](README.md#the-one-warning)) and the templates contain no examples that would lead a user to commit secrets.
2. **Malicious content in shipped example files** — if `IDENTITY.example.md`, `rules/example.md`, or `rules/example-testing.md` were tampered with to include prompt-injection that could compromise a downstream Claude Code session. The fictional persona ("Jordan Chen") in the example is deliberately benign and labeled as fiction.
3. **Claude Code loading instructions that drift from upstream** — if Claude Code changes how it discovers rules, the README's loading-mechanism documentation could mislead users. This is a stale-doc concern, not a vulnerability.

## Supported Versions

| Version  | Supported |
| -------- | --------- |
| `main`   | ✅        |
| Latest tag | ✅      |

## Reporting a Concern

If you've identified something in this scaffold that could mislead users into compromising their setup — or any other class of issue with a security flavor — please open a [GitHub Security Advisory](https://github.com/jryan5150/claude-harness-starter/security/advisories/new) (private) rather than a public issue.

For non-security concerns (typos, bad examples, outdated upstream references), open a regular issue.

## Out of scope

- Vulnerabilities in Claude Code itself — please report to [Anthropic](https://anthropic.com/security)
- Vulnerabilities in any tool you use alongside this scaffold (your editor, git, your shell, etc.)
- Process problems with how an adopter chooses to use the scaffold
