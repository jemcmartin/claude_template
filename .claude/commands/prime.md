---
description: Start of session — load the project brain and confirm state before any work
argument-hint: "[optional: FEAT_NNN you're resuming]"
---

Load context for this session. Do not write any code during this command.

## Read, in this order

1. `CLAUDE.md` — the project brain
2. `docs/CONSTITUTION.md` — the rules you must plan within
3. `FEATURE_LOG.md` — what already shipped (skim; read entries in full only if relevant)
4. If `$1` names a feature, or `CLAUDE.md` shows one in progress: that feature's
   `spec.md`, `plan.md`, and `tasks.md`
5. `docs/ARCHITECTURE.md` and `docs/GLOSSARY.md` **only if** the work ahead touches system
   structure or introduces new domain terms

## Then report back, briefly

- **Project:** one line — what this is and what "done" means
- **State:** what's built, what's in progress
- **Resuming:** if a feature is active — its status, the next unchecked task, and anything
  blocked
- **Waiting on you:** unchecked action items from `CLAUDE.md` and the active spec, flagged
  blocking vs. non-blocking
- **Stale or contradictory:** anything in the docs that conflicts with what you see in the
  repo. Say so plainly rather than silently trusting the doc — a wrong `CLAUDE.md` will
  mislead every step that follows.

Keep it under 20 lines. End by asking what we're working on, unless `$1` made that obvious —
in which case propose the next concrete step and wait for confirmation.
