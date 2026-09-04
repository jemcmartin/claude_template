# FEAT_NNN — <Feature Name>

**Status:** `Draft` | `Needs Clarification` | `Approved` | `Superseded` | `Abandoned`
**Requested:** YYYY-MM-DD
**Approved:** —
**Owner:** <!-- who decides when this is right -->

> **This document describes WHAT and WHY only.** No libraries, no schemas, no file paths, no
> API shapes — those live in [plan.md](plan.md). Written so a non-engineer could read it and
> say "yes, that's what I meant."

---

## 1. Feature Request

> Your original request, captured verbatim. Never paraphrased — the exact words are evidence
> when a later interpretation is disputed.

<!-- verbatim request -->

---

## 2. Problem and Outcome

**Problem:** <!-- What is wrong or missing today, from the user's point of view. Not a solution. -->

**Who has this problem:** <!-- Which user or role. "Everyone" usually means it isn't understood yet. -->

**Desired outcome:** <!-- What is true after this ships that isn't true now. -->

**How we'll know it worked:** <!-- The observable signal. A metric, a behaviour, a support ticket
that stops arriving. If there is no way to tell, say so explicitly. -->

---

## 3. Mockups / Diagrams

> Images you supplied, saved to `assets/`. Delete this section if there are none.

<!-- ![description](assets/mockup-01.png) -->

**Claude's interpretation:**
<!-- What Claude reads from each image: layout, components, states, interactions.
     Confirm or correct this BEFORE approving the spec — a misread mockup is the single most
     common cause of rework. -->

---

## 4. Scope

**In scope:**
- <!-- -->

**Out of scope:**
- <!-- Be specific. "Not doing password reset in this feature — FEAT_007." -->
- <!-- Naming what you are NOT building is what stops scope creep later. -->

**Assumptions:**
- <!-- Things taken as true without confirming. Each one is a place this spec could be wrong. -->

---

## 5. User Scenarios

> The feature told as behaviour. One primary path, plus what happens when things go wrong.
> Given / When / Then, in the language of the [glossary](../../GLOSSARY.md).

### Primary

**Given** <!-- starting state -->
**When** <!-- the user does this -->
**Then** <!-- this is observably true -->

### Edge cases and failures

| Situation | Expected behaviour |
|---|---|
| <!-- Network drops mid-submit --> | |
| <!-- Input is empty / malformed --> | |
| <!-- User isn't authorised --> | |
| <!-- The thing already exists --> | |

> Claude proposes this list; you correct it. Missing edge cases are where most bugs are agreed
> to in advance.

---

## 6. Requirements

### Functional

| ID | Requirement | Priority |
|---|---|---|
| FR-001 | The system MUST <!-- observable capability --> | Must |
| FR-002 | The system SHOULD <!-- --> | Should |

> MUST / SHOULD / MAY, and each one testable. "The system must be user-friendly" is not a
> requirement — it's a wish.

### Non-functional

| ID | Requirement | Target | Why |
|---|---|---|---|
| NFR-001 | <!-- e.g. Search returns results --> | <!-- under 300ms p95 --> | |
| NFR-002 | <!-- accessibility, security, offline, data retention --> | | |

> Delete rows that don't apply, but consider each: performance, security, privacy,
> accessibility, availability, observability, i18n.

---

## 7. Acceptance Criteria

> The contract. Each one is observable, binary, and becomes at least one automated test.
> The feature is not done while any of these is unverified.

| ID | Criterion | Verified by |
|---|---|---|
| AC-001 | <!-- e.g. A signed-out user visiting /dashboard is redirected to /login --> | <!-- test name, filled in during build --> |
| AC-002 | | |
| AC-003 | | |

---

## 8. Open Questions

> Everything unresolved. **The spec cannot be `Approved` while any `[NEEDS CLARIFICATION]`
> marker remains anywhere in this file.**

| # | Question | Claude's proposed default | Your answer |
|---|---|---|---|
| Q1 | | | |
| Q2 | | | |

---

## 9. Your Action Items

> Things only you can do. Claude flags which ones block the build.

| # | Item | Blocking? | Done |
|---|---|---|---|
| A1 | <!-- e.g. Create OAuth client ID --> | Yes | [ ] |
| A2 | <!-- e.g. Decide on the copy for the empty state --> | No | [ ] |

---

## 10. Dependencies

- **Depends on:** <!-- FEAT_NNN that must ship first, or external systems -->
- **Blocks:** <!-- what is waiting on this -->

---

## 11. Change Log

> Every post-approval change to this spec. This is the audit trail that keeps spec and code
> honest with each other.

| Date | Change | Why | Impact |
|---|---|---|---|
| | | | |
