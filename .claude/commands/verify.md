---
description: Check a feature against its acceptance criteria before shipping — adversarially
argument-hint: "<FEAT_NNN>"
---

Verify **$1** against its own spec. Your job in this command is to **find what's missing**, not
to confirm the work is good. Assume something was dropped and go looking for it.

## Steps

1. Read the feature's `spec.md`, `plan.md`, and `tasks.md`.
2. For each `AC-###`, find the test that verifies it and **read the test body**. A test that
   exists but asserts nothing meaningful does not count as coverage. Record the test's name in
   the spec's *Verified by* column.
3. Run the full test suite. Report the real output.
4. Run lint and type checks if the project has them.
5. Walk each edge case in spec section 5 and locate where it's actually handled. Missing
   handling is a finding, not a note.
6. Check the non-functional requirements — an `NFR` with no evidence is unverified, and
   "probably fine" is not evidence.
7. Grep the touched code for unresolved `@TODO`, `@Q`, and `@ASSUMPTION` annotations.
8. Re-run the plan's constitution check against what was actually built, not what was planned.
9. Confirm nothing out-of-scope was built.

## Report

A table of every `AC-###` with one of: **Verified** (test named), **Unverified** (no test),
**Failing**, **Manual** (steps for the user to run).

Then, plainly:

- What is genuinely done
- What is not done, or done differently from the spec
- What is untested
- What you're unsure about

If everything passes, say so without hedging. If it doesn't, say exactly what doesn't — a
verification pass that always concludes "looks good" is worth nothing. Do not update statuses
or docs here; that's `/ship`.
