---
description: Turn a feature request into a spec (WHAT and WHY) — no code, no technical design
argument-hint: "<the feature request, in your own words>"
---

Create a specification for: **$ARGUMENTS**

Write **no code** and make **no technical decisions** in this command. If you catch yourself
naming a library, a table, or a file path, that thought belongs in `plan.md` — leave it out.

## Steps

1. Read `CLAUDE.md`, `docs/CONSTITUTION.md`, `docs/GLOSSARY.md`, and skim `FEATURE_LOG.md`
   for overlap with what already exists.
2. Allocate the next `FEAT_NNN` by looking at `docs/features/`. Never reuse a number.
3. Create `docs/features/FEAT_NNN_<kebab-slug>/` and copy in
   `docs/features/_templates/spec.md`.
4. If the user supplied images, save them to that folder's `assets/`, embed them, and write
   your interpretation of each one — layout, components, states, interactions. Say explicitly
   that you need this confirmed before the spec is approved.
5. Fill in every section.

## While writing

- **Capture the request verbatim** in section 1. Your paraphrase goes in section 2, never over
  the top of their words.
- **Mark every gap** as `[NEEDS CLARIFICATION: <specific question>]` inline where it matters,
  and add a row to section 8 with your proposed default. Do not guess and move on
  (Constitution, Article II). Common places gaps hide: who is allowed to do this, what happens
  on failure, what the empty state shows, limits and quotas, what happens to existing data.
- **Write acceptance criteria a test could fail.** "Works correctly" is not a criterion.
  Aim for the smallest set that fully pins the behaviour — usually 4–10.
- **Be aggressive about out-of-scope.** Everything adjacent that you are *not* building goes in
  section 4. This is what stops the feature growing later.
- **Propose the edge cases** in section 5 yourself. Network failure, empty input, unauthorised
  user, duplicate, concurrent edit, very large input. The user corrects the list; they rarely
  produce it unprompted.
- **Use the glossary's exact terms.** If you need a new one, propose adding it rather than
  inventing a synonym.

## Then

Report back: the feature ID and path, a two-line summary, the open questions numbered, and the
blocking action items. Set status to `Needs Clarification` if any question is open, `Draft`
otherwise.

Do not start planning. The user approves the spec first.
