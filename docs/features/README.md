# Features

One folder per feature. Everything about a feature — what it is, how it will be built, the task
list, and the images you sent — lives together and stays in git next to the code it produced.

```
docs/features/
  _templates/
    spec.md       WHAT and WHY   — no implementation detail
    plan.md       HOW            — technical approach, decisions, risks
    tasks.md      DO             — ordered, checkable units of work
  FEAT_001_user-login/
    spec.md
    plan.md
    tasks.md
    assets/       mockups, diagrams, screenshots you supplied
```

## Numbering

`FEAT_NNN_kebab-slug`, zero-padded, allocated in order, **never reused** — not even for a feature
that was abandoned. A dead `FEAT_014` folder with `Status: Abandoned` and one line explaining why
is more useful than a gap.

## The four states a feature moves through

| Phase | Artefact | Gate before moving on |
|---|---|---|
| Specify | `spec.md` | No `[NEEDS CLARIFICATION]` left; you approved the acceptance criteria |
| Plan | `plan.md` | Approach agreed; constitution check passes; blocking action items known |
| Task | `tasks.md` | Every `AC-###` is covered by at least one task |
| Implement | code + tests | Every task checked; every `AC-###` verified; docs updated |

Gates exist so mistakes are caught while they are still cheap to fix — a wrong sentence in a spec
costs a minute, the same mistake in merged code costs a day.

## Rules

- **Spec contains no implementation detail.** No library names, no schema, no file paths. If you
  can't describe it without naming a technology, it belongs in `plan.md`.
- **IDs are stable and referenced everywhere.** `FR-###` requirements, `NFR-###` non-functionals,
  `AC-###` acceptance criteria, `T-###` tasks, `R-###` risks. Tasks cite the `AC-###` they serve;
  tests cite the `AC-###` they verify. That chain is how you know nothing was dropped.
- **Change the spec, don't drift from it.** If the build reveals the spec was wrong, edit the
  spec, note it in *Change Log*, and carry on. A spec that no longer describes the code is worse
  than no spec.
- **Assets are referenced, not pasted.** Images go in `assets/` and are embedded with relative
  markdown links.
