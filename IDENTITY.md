# Identity — [Your Name]

> **Layer 1 of the harness.** Your building philosophy.
> Stable across projects. Personal, not prescriptive.
> Fill in over weeks, not an afternoon.

---

## How to Use This File

This is the slowest-moving layer of your harness. It's the thing your
rules and projects inherit _from_. Nothing here should be aspirational —
only things you've already proven to yourself across multiple projects.

Refuse to fill in a section until you have real conviction about it.
An empty section is better than a placeholder that sounds right but
doesn't guide your decisions.

---

## Foundational Axioms

> What do you hold to be true about building software? Not best practices —
> **convictions**. Things you'd defend in an argument. Things that have
> saved you pain across multiple projects.

Examples of the _shape_ (not the content — write your own):

- "Simplicity is load-bearing, not a virtue."
- "Every system has a failure mode; design for it before the first user arrives."
- "Intelligence should be the substrate, not a feature bolted onto an existing stack."

<!-- Your 3-5 axioms here. Resist writing more than 5. -->

---

## Patterns You See Across Your Work

> When you've built many systems, some patterns recur.
> These are patterns **you** use — not patterns the industry uses.
>
> A best practice is what everyone does.
> A pattern is what _you_ do, identified after the fact by looking at
> what your systems have in common.

Examples of the shape:

- "I always separate orchestration from execution."
- "I use a log-structured append-only store for anything I might want to replay."
- "Every feature module exports a diagnostics function."

<!-- Your patterns here. 3-7. -->

---

## The Design Validation Wall

> When you're evaluating a new architecture or a new design,
> what questions do you bounce it against?
>
> These are the questions that protect you from building the wrong thing.
> Keep the list short — these are the ones you _always_ ask,
> not every question you might ever want to.

| Challenge | Question                                    |
| --------- | ------------------------------------------- |
| Example   | Is this the simplest thing that works?      |
| Example   | What does it fail like when it fails?       |
| Example   | How long until this becomes unmaintainable? |

<!-- Your validation questions. 5-10. -->

---

## When NOT to Apply This Framework

> **The most important section.** When is your own philosophy the wrong lens?
>
> If you can't answer this, your philosophy is too universal and will
> betray you in edge cases. Every framework has a domain of applicability.
> Name yours.
>
> Examples: "This philosophy is wrong for throwaway scripts."
> "This is overkill for internal tooling with <5 users."
> "This framework assumes I'm the long-term maintainer; don't use it
> for code I'm handing off."

<!-- Your answer. Be specific about scope limits. -->

---

## What I'm Still Figuring Out

> Optional section, but useful.
> Your philosophy is not done. What questions do you still hold open?
> Revisiting these each quarter is how Layer 1 evolves.

<!-- Open questions. -->

---

## Version History

- **v0.1** — Initial scaffold, [date]
- <!-- Add entries when you make meaningful updates -->
