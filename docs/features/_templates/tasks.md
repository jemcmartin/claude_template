# FEAT_NNN — Tasks

**Spec:** [spec.md](spec.md) · **Plan:** [plan.md](plan.md)
**Last updated:** YYYY-MM-DD

> The ordered, checkable breakdown. Generated from the plan **after** it's approved.
>
> A good task is one Claude can complete in a single focused pass and you can verify without
> reading the whole diff. If a task needs a decision from you, it isn't a task — it's an open
> question that belongs back in the spec.

---

## Progress

`░░░░░░░░░░` 0 / 0 complete

| Status | Count |
|---|---|
| Done | 0 |
| In progress | 0 |
| Blocked | 0 |
| Not started | 0 |

---

## Conventions

- **ID** — `T-###`, allocated in order, never reused.
- **Serves** — the `AC-###` or `FR-###` this task exists for. Every task serves something; a task
  that serves nothing is scope creep and gets deleted.
- **Deps** — task IDs that must finish first.
- **P** — `[P]` marks tasks safe to run in parallel: they touch disjoint files and share no deps.
- Tasks are listed in dependency order. **Setup → tests → implementation → integration → polish.**

---

## Tasks

### Setup

| ID | P | Task | Serves | Deps | Files | Status |
|---|---|---|---|---|---|---|
| T-001 | | <!-- e.g. Add migration for `sessions` table --> | FR-001 | — | | [ ] |

### Tests

> Written from the acceptance criteria, before or alongside the implementation they cover
> (see Constitution, Article IV).

| ID | P | Task | Serves | Deps | Files | Status |
|---|---|---|---|---|---|---|
| T-010 | [P] | <!-- e.g. Test: signed-out user hitting /dashboard redirects to /login --> | AC-001 | T-001 | | [ ] |

### Implementation

| ID | P | Task | Serves | Deps | Files | Status |
|---|---|---|---|---|---|---|
| T-020 | | | AC-001 | T-010 | | [ ] |

### Integration & Polish

| ID | P | Task | Serves | Deps | Files | Status |
|---|---|---|---|---|---|---|
| T-090 | | Update `CLAUDE.md`, `FEATURE_LOG.md`, and any architecture docs | — | all | | [ ] |

---

## Coverage Check

> Run before starting implementation. Every acceptance criterion must have at least one task.
> A blank cell here is a feature that will ship incomplete.

| AC | Covered by | Verified |
|---|---|---|
| AC-001 | T-010, T-020 | [ ] |
| AC-002 | | [ ] |

---

## Blocked / Deferred

| ID | Blocked by | Since | Decision needed from |
|---|---|---|---|
| | | | |

> Anything deferred at completion must leave here with a home: a new `FEAT_` spec, a
> `Known Debt` row in `ARCHITECTURE.md`, or an explicit "won't do".

---

## Session Notes

> Short running log. Claude appends one line per working session so a new session can pick up
> mid-feature without re-deriving where things stand.

| Date | Did | Next |
|---|---|---|
| | | |
