# Identity — Jordan Chen (example)

> ⚠️ **This is a FICTIONAL persona** shown as an example of a filled
> `IDENTITY.md`. It exists to demonstrate the shape and tone, NOT to
> be copied. Your convictions should look nothing like Jordan's.
> Ignore or delete this file once you've written your own.

---

## About This Example

Jordan Chen is a senior web application developer with 8 years of experience
building B2B SaaS products on Node.js, TypeScript, and React. The persona is
deliberately ordinary — no exotic background, no specialty framework — so the
example teaches the **format and tone**, not the content.

Notice how every section has specific, defensible statements. Nothing says
"I value quality" or "I believe in clean code." Those phrases reveal nothing
about how Jordan actually makes decisions. Your `IDENTITY.md` should share
that specificity.

---

## Foundational Axioms

- **Boring technology is a feature.** Postgres over Cassandra, server-rendered
  HTML over SPA where possible, Node over the language-of-the-month. Novel
  tools create novel failure modes, and I can only pay down so many.

- **User-perceived performance beats measured performance.** A 500ms load that
  shows a skeleton at 50ms feels faster than a 200ms load with a blank screen.
  Design for perception before optimizing actuals.

- **Every external dependency is a future liability.** Adding a library is not
  free. It's a bet that the maintainer will still care about it when I'm
  debugging it at 2 AM in 2028. Audit the maintainer before the code.

- **Feature flags are not optional for user-facing changes in production.**
  If I can't turn something off without a deploy, I can't operate it.

---

## Patterns You See Across Your Work

- I separate HTTP handlers from business logic in every project. Handlers are
  glue; they must be dumb. All testing effort goes into the logic layer.

- Every feature flag has a removal date written into the flag name or an
  adjacent comment. Flags without removal dates become permanent technical
  debt.

- I use structured logging (JSON) in every service. Plain-text grep-friendly
  logs are a lie I tell myself until log volume becomes real.

- I put the "why" in Git commit messages, not in code comments. Code shows
  what; commits show why. Comments in code rot because nobody updates them.

---

## The Design Validation Wall

| Challenge       | Question                                            |
| --------------- | --------------------------------------------------- |
| Reversibility   | Can I ship this behind a feature flag?              |
| Blast radius    | What happens when this fails at 3 AM?               |
| Maintainability | Will my future self understand this in 6 months?    |
| Scope           | Is this the simplest thing that actually works?     |
| Observability   | How will I know it's broken before a user tells me? |
| Succession      | If I leave tomorrow, can the next person own this?  |

---

## When NOT to Apply This Framework

- **Exploratory prototypes.** Code that will live 3 days doesn't need feature
  flags, structured logging, or observability infrastructure. Learning is
  the output; the code is scaffolding.

- **Internal tools with under 5 users.** 3 AM failure? I'll look at it at
  9 AM. The SLA is my attention, not a contract.

- **Code I'm handing off long-term.** My preferences aren't universal.
  If I'm not the maintainer, my philosophy is baggage for the next person.
  Match the style to the successor.

---

## What I've Changed My Mind About

- **I used to think "use the fanciest framework available."** Now I think
  "use the framework the next hire will already know." Hiring speed is an
  architectural constraint more real than benchmark results.

- **I used to think 100% test coverage was the goal.** Now I think "tests
  that fail when the system is actually broken" is the goal. Coverage is
  a proxy, not a target, and optimizing the proxy wastes weeks.

- **I used to believe microservices were the end state.** Now I think a
  well-organized monolith is the correct answer 90% of the time, and
  microservices are a specific response to scale problems I mostly
  don't actually have.

---

## What I'm Still Figuring Out

- When to stop refactoring a codebase and start rewriting it.
- How to balance consistency with team velocity when three developers
  disagree on style.
- Whether "you build it, you run it" scales past 30 engineers without
  becoming an operational burden that crushes feature velocity.

---

## Version History

- **v0.1** — Initial fictional persona, created as a reference example.
