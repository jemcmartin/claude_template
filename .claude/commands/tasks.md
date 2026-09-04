---
description: Break an approved plan into ordered, verifiable tasks
argument-hint: "<FEAT_NNN>"
---

Generate the task breakdown for **$1**.

Stop if the plan isn't `Approved`, or if it still has unresolved unknowns in section 3.

## Steps

1. Read the feature's `spec.md` and `plan.md`.
2. Copy `docs/features/_templates/tasks.md` into the feature folder and fill it in.

## What makes a good task here

- **One focused pass.** Completable without stopping to ask a question. If a task needs a
  decision from the user, it is not a task — it's an open question that goes back to the spec.
- **Verifiable on its own.** You can state what "done" looks like for it in one line.
- **Names its files.** Concrete paths, so parallel-safety is checkable rather than assumed.
- **Serves something.** Every task cites the `AC-###` or `FR-###` it exists for. A task serving
  nothing is scope creep — delete it.

## Ordering

Setup → tests → implementation → integration → polish. Within that, dependency order. Mark
`[P]` only where tasks touch genuinely disjoint files and share no dependency.

Include tasks for the unglamorous work that otherwise gets skipped: migrations, error handling,
the empty state, observability, and the docs updates in the plan's Definition of Done.

## Coverage check — do this, don't skip it

Fill in the coverage table and confirm **every** `AC-###` from the spec maps to at least one
task. If one doesn't, either you missed a task or the AC is untestable. Say which, and fix it
before reporting done.

## Then

Report: task count, the critical path, what can run in parallel, and any AC you couldn't cover
cleanly. Ask before starting implementation.
