# Project Constitution

> The non-negotiable rules of this project. Claude reads this before planning any feature and
> **must refuse to produce a plan that violates it** — instead it raises the conflict and asks
> you to either change the plan or amend this file.
>
> Keep this short. Everything here costs context on every planning pass. If a rule isn't worth
> enforcing on every feature, it belongs in `ARCHITECTURE.md` or a feature plan instead.

**Version:** 1.0.0
**Last amended:** <!-- YYYY-MM-DD -->

---

## How to amend

Principles change as the project learns. To change one:

1. Say what you want changed and why.
2. Claude proposes the edit plus a list of already-shipped features that now violate it.
3. You approve. Claude bumps the version, dates the amendment, and logs it below.

Amendments are **never** made silently mid-feature.

| Version | Date | Change | Why |
|---|---|---|---|
| 1.0.0 | | Initial constitution | Project kickoff |

---

## Article I — Specification precedes code

No production code is written before an approved spec exists for the work.

- The spec defines **what** and **why**. The plan defines **how**. Code is the output of both.
- If implementation reveals the spec was wrong, **stop and amend the spec**, then continue.
  Code and spec never diverge silently.
- Trivial changes (typo, dependency bump, formatting) are exempt. If you have to argue about
  whether something is trivial, it isn't.

## Article II — Ambiguity is surfaced, never guessed

When a requirement is underspecified, Claude marks it `[NEEDS CLARIFICATION: <question>]` in the
spec rather than picking an answer.

- A spec with open `[NEEDS CLARIFICATION]` markers cannot reach `Approved`.
- Where a reasonable default exists, Claude may propose it — as a marked assumption in the spec,
  not as a silent decision buried in code.

## Article III — Acceptance criteria are testable and traceable

Every acceptance criterion is written so a test can pass or fail against it.

- Criteria are observable behaviour, not implementation ("user sees an error message" — not
  "the validator returns false").
- Every `AC-###` maps to at least one automated test. Every test names the `AC-###` it covers.
- A feature is not `Complete` while any acceptance criterion is unverified.

## Article IV — Tests are written against the spec, not the implementation

Tests are derived from acceptance criteria before or alongside the code, never reverse-engineered
from whatever the code happens to do.

- A test that was changed to match a bug is a spec change and needs the same approval.
- Bug fixes start with a failing test that reproduces the bug.

<!-- Amend this article to match how strictly you want to work. Options, from strict to loose:
     - Strict TDD: tests written and failing before implementation.
     - Test-alongside: tests land in the same change as the code.
     - Test-after-with-gate: implementation may land first, but the feature cannot be marked
       Complete until coverage exists.
     Pick one and state it here so Claude stops asking. -->

**This project's rule:** <!-- e.g. Test-alongside -->

## Article V — Simplicity is the default

Claude builds the simplest thing that satisfies the spec.

- No abstraction is introduced for a single caller. No framework is added for a single use.
- No speculative extensibility. Requirements not in the spec are not built "just in case".
- Every new dependency is named in the plan with a one-line justification, and you approve it.

## Article VI — Decisions are recorded where they can be found

Any decision that a future reader would otherwise reverse by accident gets written down.

- Architecture-level and hard-to-reverse decisions → an ADR in [docs/adr/](adr/).
- Feature-scoped decisions → the plan's *Decisions* section.
- Claude does not reverse a recorded decision without raising it first.

## Article VII — The project brain stays current

`CLAUDE.md` reflects the project as it is right now, not as it was at kickoff.

- Stale is worse than absent: an incorrect statement in `CLAUDE.md` misleads every future session.
- Claude updates `CLAUDE.md` and `FEATURE_LOG.md` as part of finishing a feature, not as a
  separate chore that gets skipped.

## Article VIII — Scope is explicit and bounded

Every spec states what is **out of scope** as clearly as what is in scope.

- Claude does not widen scope mid-feature. New ideas become new `FEAT_` specs.
- Claude does not narrow scope silently either. If something in the spec turns out to be blocked,
  it says so explicitly rather than shipping a partial feature as if it were whole.

---

## Project-Specific Articles

> Rules unique to this project — added during kickoff and as you learn.
> Examples of the kind of thing that belongs here:
> "All money is stored in integer minor units, never floats."
> "No PII leaves the EU region."
> "Every API response shape is defined in the OpenAPI schema before the handler is written."
> "The app must remain usable offline."

<!-- Add project articles below. Delete this comment once you have at least one. -->
