---
description: Build the next tasks for a feature, keeping spec, tasks, and code in step
argument-hint: "<FEAT_NNN> [task IDs, e.g. T-010 T-020]"
---

Implement tasks for **$1**. If task IDs were given, do exactly those. Otherwise take the next
unblocked tasks in dependency order and stop at a natural checkpoint rather than running
through the whole list in one go.

## Before writing code

1. Read the feature's `spec.md`, `plan.md`, and `tasks.md`, plus `docs/CONSTITUTION.md`.
2. Check the blocking action items in the spec are done. If a blocking item is outstanding, say
   so and work on something else rather than stubbing around it.
3. Read the existing code you're about to change. Match its conventions — naming, structure,
   error handling, comment density. Code that reads like it was written by a different person
   is a cost paid on every future edit.

## While building

- Follow the plan. If the plan turns out to be wrong, **stop and say so** — don't quietly build
  something different. A five-line message now beats a surprise in the diff.
- Write tests from the acceptance criteria, per Constitution Article IV. Name the `AC-###` in
  the test name or a comment on it, so the trace survives.
- Stay inside the task's scope. Something broken but unrelated gets flagged, not fixed
  in passing — it goes in the plan's risks, `Known Debt`, or a new spec.
- Don't add abstraction for one caller, and don't build for requirements that aren't in the
  spec (Article V).
- Never fake a passing test, weaken an assertion, or special-case a test input to get green.
  If a test won't pass, the honest report is more useful than the green tick.

## After each task

- Tick it in `tasks.md` and update the progress counts.
- Append one line to *Session Notes*: what you did, what's next.
- Run the relevant tests. If they fail, fix or report — never leave a knowingly broken tree
  without saying so.

## Then report

- Tasks completed, tasks remaining
- Test results — actual output, including failures
- Anything you had to decide that wasn't in the plan, and why
- Anything that now looks wrong in the spec or plan
- What you'd do next

Do not mark the feature complete here. That's `/verify` then `/ship`.
