---
description: Close out a verified feature and bring every living document back into step
argument-hint: "<FEAT_NNN>"
---

Close out **$1**.

## Precondition

`/verify` has passed for this feature. If it hasn't, or if any acceptance criterion is
unverified, stop and say what's outstanding. Do not close out a feature that isn't done —
a `FEATURE_LOG` full of half-finished entries is how a project loses track of itself.

## Update, in this order

1. **The feature folder**
   - `spec.md` → every `AC-###` has its verifying test named
   - `plan.md` → Definition of Done fully checked, or an explicit note for anything deferred
   - `tasks.md` → all tasks checked or moved to Deferred with a reason and a destination

2. **`CLAUDE.md`**
   - *Current State* — move this feature into "what's been built"; set what's in progress next
   - *Pending Action Items* — tick what's done, remove what's obsolete, add anything new
   - *Architecture Decisions* — add rows for decisions made, linking any ADR

3. **`FEATURE_LOG.md`** — a new entry at the top: what was built, the decisions worth
   remembering, what was deferred, and files touched. Write it for someone with no memory of
   this week.

4. **`docs/ARCHITECTURE.md`** — only if structure actually changed: components, data model,
   flows, invariants, or a new `Known Debt` row.

5. **`docs/GLOSSARY.md`** — any new domain terms this feature introduced.

6. **ADRs** — write one for any hard-to-reverse decision that doesn't have one yet, and add it
   to the ADR index.

## Deferred work

Everything deferred leaves with a home: a new `FEAT_` spec, a `Known Debt` row, or an explicit
"won't do" recorded in the log. Nothing gets to live only in the conversation — this session's
context disappears; the repo is what survives.

## Then

Report what you changed, and propose the next feature with a one-line reason. Suggest a commit
message; only commit if the user asks.
