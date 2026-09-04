---
description: Interview the user and populate CLAUDE.md and the project constitution
---

Set up this project's brain. This is a **conversation**, not a form. Ask about one area at a
time, react to the answers, and follow up where something is vague. Do not write any files
until the interview is done and the user has confirmed.

First read `CLAUDE.md`, `docs/CONSTITUTION.md`, and `docs/ARCHITECTURE.md` so you know what
needs filling.

## Interview, one area at a time

1. **The product.** What is being built, for whom, and what problem it removes. Push until you
   can state it in one sentence back to them.
2. **Done.** What has to be true for v1 to be finished. If they can't say, help them cut it
   down to something that can be.
3. **Users and scenarios.** Who uses it and the two or three things they actually do with it.
4. **Tech stack.** Frontend, backend, data, auth, hosting, testing. **Unknown is a valid
   answer** — record it as a decision to make, don't push them into choosing now.
5. **Constraints.** Deadlines, budget, compliance, existing systems, team size, things that
   are off the table.
6. **Working style.** How strict on tests (this sets Constitution Article IV), how much they
   want to review, how they feel about new dependencies.
7. **Domain vocabulary.** The nouns they keep using. Watch for two words meaning one thing, or
   one word meaning two — surface the collision now.
8. **Prerequisites.** Accounts, keys, environments they'll need to set up.

## Then write

- `CLAUDE.md` — every section, no placeholders left. Note unknowns explicitly as unknowns.
- `docs/CONSTITUTION.md` — fill Article IV's testing rule and add any project-specific
  articles their constraints imply. Set version 1.0.0 and today's date.
- `docs/GLOSSARY.md` — the vocabulary from step 7.
- `docs/ARCHITECTURE.md` — only what they actually know now. Leave the rest for the first
  feature to establish; a speculative diagram is worse than an empty section.

Finish by showing what you wrote, then say what the first feature should probably be and why —
and let them disagree.
