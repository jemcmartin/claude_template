---
description: Work through a spec's open questions until it can be approved
argument-hint: "<FEAT_NNN>"
---

Resolve the open questions in the spec for **$1**.

1. Read that feature's `spec.md`, plus `CLAUDE.md` and `docs/CONSTITUTION.md`.
2. Collect every `[NEEDS CLARIFICATION]` marker and every unanswered row in section 8.
3. Ask them **one at a time**, highest-impact first — the ones that would change the shape of
   the feature before the ones that change a detail. Batching ten questions into one message
   gets ten shallow answers.
4. For each, give your recommended default and the trade-off in one line, so the user can say
   "yes, that one" instead of writing an essay.
5. After each answer: update the spec immediately — remove the marker, fill in the answer, and
   propagate the consequence into scope, scenarios, requirements, and acceptance criteria.
   An answer that only lands in section 8 has been half-recorded.
6. If an answer contradicts something already in the spec, say so and fix both places.
7. If an answer reveals a whole area nobody had considered, add new `[NEEDS CLARIFICATION]`
   markers rather than quietly absorbing it.

When no markers remain, re-read the whole spec end to end and check:

- Every requirement is testable
- Every acceptance criterion is observable and binary
- Out-of-scope is specific
- No implementation detail leaked in

Then show the user a short diff-style summary of what changed and ask them to approve. On
approval, set `Status: Approved`, stamp the date, and stop. Planning is a separate command.
