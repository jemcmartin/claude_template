# FEAT_NNN — Technical Plan

**Status:** `Draft` | `Approved` | `Revised`
**Spec:** [spec.md](spec.md)
**Last updated:** YYYY-MM-DD

> **HOW the spec gets built.** Written after the spec is `Approved`, before any task list.
> If writing this reveals the spec is wrong or incomplete, stop and fix the spec first —
> do not paper over a spec gap with a technical decision.

---

## 1. Constitution Check

> Run before anything else. Claude checks this plan against [CONSTITUTION.md](../../CONSTITUTION.md)
> and states the result. A violation is not a warning to note and move past — it either changes
> the plan or it amends the constitution, and the amendment is yours to approve.

| Article | Compliant? | Note |
|---|---|---|
| I — Spec precedes code | | |
| II — Ambiguity surfaced | | |
| III — Testable, traceable criteria | | |
| IV — Tests from spec | | |
| V — Simplicity | | |
| VI — Decisions recorded | | |
| VII — Brain stays current | | |
| VIII — Scope bounded | | |
| Project articles | | |

**Result:** `Pass` | `Pass with justified exception` | `Blocked — needs your decision`

**Justified exceptions:**
<!-- Each one: which article, why the simpler compliant option was rejected, what we accept
     as a result. An exception with no cost stated is not an exception, it's a shortcut. -->

---

## 2. Approach

**Recommended approach:**
<!-- Two or three paragraphs. What gets built, in what shape, and why this shape. -->

**Alternatives considered:**

| Option | Why not |
|---|---|
| | |

> Recording rejected options stops the same debate happening again in three months, and stops
> Claude re-proposing something you already ruled out.

**Why this is the simplest thing that works:**
<!-- Article V. If it isn't simple, justify the complexity here. -->

---

## 3. Research and Unknowns

> Anything the plan depends on that isn't yet known. Resolve these before the task breakdown —
> an unknown carried into implementation becomes a rewrite.

| # | Unknown | How we'll resolve it | Resolved? | Finding |
|---|---|---|---|---|
| U1 | <!-- e.g. Does the payment SDK support partial refunds? --> | <!-- spike / read docs / ask --> | | |

---

## 4. Design

### Components touched

| Component | New / Changed | What changes |
|---|---|---|
| | | |

### Data

<!-- Schema changes, new entities, migrations. Name the entities using the terms in
     ../../GLOSSARY.md — add new terms there rather than inventing them here. -->

**Migration required:** Yes / No
**Backwards compatible:** Yes / No — <!-- if no, what's the rollout order? -->

### Interfaces

<!-- API endpoints, events, function signatures, CLI surface — whatever this feature exposes to
     something else. Contracts first: agreeing the shape here is far cheaper than discovering
     a mismatch during integration. -->

### Flow

<!-- The end-to-end path through the system for the primary scenario in the spec.
     Numbered steps or a mermaid sequence diagram. -->

---

## 5. Decisions

> Feature-scoped decisions. Anything architecture-level or hard to reverse gets an
> [ADR](../../adr/) instead, and is linked here.

| # | Decision | Why | Reversible? |
|---|---|---|---|
| D1 | | | |

---

## 6. New Dependencies

> Every addition needs a reason and your approval. The cheapest dependency is the one not added.

| Package | Version | Why | Alternative rejected | Licence | Approved |
|---|---|---|---|---|---|
| | | | | | [ ] |

---

## 7. Risks

| ID | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R-001 | | Low/Med/High | Low/Med/High | |

> Include the boring ones: data loss on migration, a rate limit you'll hit, a third party that
> goes down, a change that can't be rolled back.

---

## 8. Test Strategy

> How each acceptance criterion gets verified. Every `AC-###` from the spec appears here.

| AC | Test type | What it asserts | Where |
|---|---|---|---|
| AC-001 | Unit / Integration / E2E / Manual | | <!-- path/to/test --> |

**Manual verification** (only for what genuinely cannot be automated):
- [ ] <!-- step, and what you should see -->

**Test data / fixtures needed:**
<!-- -->

---

## 9. Rollout

**Feature flag:** Yes / No — <!-- name -->
**Rollout order:** <!-- e.g. migration → backend → flag on for internal → general release -->
**How we roll back:** <!-- Concretely. "Revert the commit" is only true if there's no migration. -->
**What we watch after release:** <!-- log, metric, alert -->

---

## 10. Definition of Done

- [ ] Every `AC-###` verified and its test named in the spec's *Verified by* column
- [ ] Every task in [tasks.md](tasks.md) checked off or explicitly deferred with a reason
- [ ] All tests pass; no new lint or type errors
- [ ] No `@TODO` or `@Q` annotations left unresolved in the touched code
- [ ] `CLAUDE.md` — current state, pending action items, and decision index updated
- [ ] `ARCHITECTURE.md` / `GLOSSARY.md` / ADRs updated if this changed structure or vocabulary
- [ ] `FEATURE_LOG.md` entry written
- [ ] Deferred work captured as new `FEAT_` specs or `Known Debt` rows, not left in someone's head
