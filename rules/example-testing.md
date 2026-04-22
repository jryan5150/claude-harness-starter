# Testing (example rule file)

_Applies to: all dev work_

---

> **Second worked example.** The first example (`example.md`) covers git
> workflow. This one covers testing discipline. Together they demonstrate
> the format is domain-agnostic — you can write a rule file about anything
> that recurs across projects.

---

## Test-First for Bug Fixes

- Write the failing test FIRST. Only then fix the code.
- The failing test proves you understood the bug.
- A bug without a regression test is a bug waiting to return.

## Test Structure

- Arrange → Act → Assert. In that order, visibly.
- One assertion per test when possible.
- Descriptive names that read as specifications:
  `it("returns 401 when token is expired")`, not `testAuth()`.

## What to Mock

- Mock external services: third-party APIs, payment processors, email providers.
- Never mock the code under test — that tests nothing.
- Prefer real databases in integration tests, even if it means a SQLite
  or containerized Postgres for the test run. Mocks lie; real databases
  fail the same way production does.

## What Not to Test

- Framework behavior. I don't need to test that Express routes a GET.
- Third-party libraries. Trust them or don't use them.
- Trivial getters and setters. Test the behavior they enable, not the accessors.

## Flaky Tests

- A flaky test is a broken test. Fix it or delete it.
- Never merge a `skip` or `xit` into the main branch.
- "Just rerun CI" is how you train yourself to ignore real failures.

## Coverage

- Coverage is a diagnostic, not a goal.
- 80%+ is a floor for production code, not a target.
- Critical paths (auth, payments, data processing) demand 95%+ plus
  specific hostile-case tests.

---

## Notes on This Second Example

Notice the structural differences from `example.md`:

- Different domain (testing vs. git).
- Different section count (7 sections vs. 4).
- Slightly different voice — more opinionated in places.

The point: **rule files don't need to follow a rigid schema.** Each file
should be whatever shape makes its domain clearest. The only constants
are: short, actionable, scoped with a header, no theory.
