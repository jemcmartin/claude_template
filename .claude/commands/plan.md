---
description: Produce the technical plan for an approved spec
argument-hint: "<FEAT_NNN>"
---

Write the technical plan for **$1**.

## Preconditions — check these first, and stop if they fail

- The spec exists and its status is `Approved`.
- No `[NEEDS CLARIFICATION]` markers remain.

If either fails, say so and run the clarification conversation instead. Planning against an
unapproved spec produces work that gets thrown away.

## Steps

1. Read: the spec, `CLAUDE.md`, `docs/CONSTITUTION.md`, `docs/ARCHITECTURE.md`,
   `docs/GLOSSARY.md`, and any ADR the feature touches.
2. **Read the actual code** in the areas this feature touches before proposing anything. A plan
   written from the docs alone will contradict the repo.
3. Copy `docs/features/_templates/plan.md` into the feature folder and fill it in.

## While planning

- **Run the constitution check first**, not last. If the natural approach violates an article,
  surface it now: either change the approach or ask the user to amend the constitution. Never
  record a violation and proceed.
- **Prefer what already exists.** Reuse the patterns, helpers, and conventions in the repo over
  introducing new ones. Name the existing thing you're extending.
- **Justify every new dependency** and name the alternative you rejected, including "write it
  ourselves."
- **List unknowns honestly** in section 3 and resolve them before the plan is approved. If
  something needs a spike, say so and propose the smallest experiment that settles it.
- **Map every `AC-###` to a test** in section 8. If an AC has no viable test, that's a signal
  the AC is badly written — go back and fix the spec.
- **Say how it rolls back.** Especially with migrations.
- If planning reveals the spec is wrong or incomplete: **stop, fix the spec, log it in the
  spec's change log**, then resume. Do not compensate for a spec gap with a technical decision.

## Then

Report: the recommended approach in three sentences, the constitution result, new dependencies
needing approval, the top risks, and any unresolved unknowns.

Ask for approval. Do not write the task breakdown or any code yet.
