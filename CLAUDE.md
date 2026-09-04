# CLAUDE.md — Project Brain

> **This file starts blank. Don't fill it in by hand.**
> Run `/kickoff` and let Claude interview you.
>
> Claude loads this file at the start of every session, so it is the single most valuable
> document in the repo — and the most expensive to get wrong. Keep it **short and true**.
> Detail belongs in the documents it points to. A stale line here misleads every future
> session; when in doubt, delete rather than let it rot.

---

## Operating Rules

> How Claude works in this repo. These apply to every session, before anything else.

1. **Read before writing.** At session start read this file and `docs/CONSTITUTION.md`, plus
   the active feature's `spec.md` / `plan.md` / `tasks.md` if one is in progress. `/prime`
   does this.
2. **Spec before code.** Non-trivial work follows the pipeline:
   `/specify` → `/clarify` → `/plan` → `/tasks` → `/implement` → `/verify` → `/ship`.
   Each phase gates the next. Skipping a gate is the user's call to make, not Claude's.
3. **Surface ambiguity, never guess.** Underspecified requirements get
   `[NEEDS CLARIFICATION: <question>]` in the spec. A proposed default is fine — a silent
   decision buried in code is not.
4. **The constitution is binding.** If a plan violates `docs/CONSTITUTION.md`, raise the
   conflict. Change the plan or amend the constitution; never proceed past it quietly.
5. **Keep the documents in step with the code.** Spec, plan, tasks, and this file are updated
   as part of the work, not afterwards. If the build proves the spec wrong, fix the spec.
6. **Report honestly.** Failing tests are reported with their output. Skipped steps are named.
   Never weaken a test to make it pass, and never claim verification you didn't do.
7. **Stay in scope.** Unrelated problems get flagged, not fixed in passing.

---

## Project Overview

**What is this?**
<!-- One paragraph. What it is, who it's for, what problem it removes. -->

**What does "done" look like?**
<!-- The v1 finish line, concretely enough to tell whether you've crossed it. -->

**Who uses it:**
<!-- Roles and what each one actually does with it. -->

---

## Tech Stack

| Layer | Choice | Why | Status |
|---|---|---|---|
| Frontend | | | Decided / Undecided |
| Backend | | | |
| Database | | | |
| Auth | | | |
| Hosting | | | |
| Testing | | | |

**Key constraints:**
<!-- Deadlines, compliance, budget, existing systems, things ruled out. -->

**Undecided:** <!-- List them plainly. A recorded unknown is useful; a forgotten one is a trap. -->

---

## Current State

**Shipped:**
<!-- Feature IDs and one line each. Detail lives in FEATURE_LOG.md. -->

**In progress:**
<!-- FEAT_NNN, its phase, and where it stopped. -->

**Next up (rough):**
<!-- Direction, not commitment. -->

---

## Pending Action Items

> Things **you** must do. Claude can't. Blocking items stop a build; non-blocking ones don't.

| # | Item | Blocking | Needed for | Done |
|---|---|---|---|---|
| | | | | [ ] |

---

## Architecture Decisions

> Index only — one line each. Full reasoning lives in `docs/adr/`.
> Claude does not reverse anything listed here without raising it first.

| Decision | Rationale | ADR | Date |
|---|---|---|---|
| | | | |

---

## How to Run This Project

```bash
# Install
# Run locally
# Run tests
# Lint / typecheck
```

<!-- Keep these commands working. Claude runs them; wrong commands waste a whole session. -->

---

## Map of the Repo

| Path | What's there |
|---|---|
| `docs/CONSTITUTION.md` | Non-negotiable project rules. Read before planning. |
| `docs/ARCHITECTURE.md` | System shape, components, data model, invariants, known debt. |
| `docs/GLOSSARY.md` | Domain vocabulary. Specs, code, and UI use these exact terms. |
| `docs/adr/` | Architecture decision records. |
| `docs/features/` | One folder per feature: spec, plan, tasks, assets. |
| `FEATURE_LOG.md` | Archive of what shipped and why. |
| `.claude/commands/` | The workflow commands. |
| <!-- src/ etc. --> | <!-- fill in as the codebase grows --> |

---

## Code Annotation Conventions

> Leave these anywhere — source, docs, config. Claude acts on them during `/annotations` and
> flags any left unresolved during `/verify`.

| Decorator | Intent | Claude's behaviour |
|---|---|---|
| `@TODO` | An action for Claude | Execute if the intent is unambiguous and the change is contained. Otherwise ask first. Remove once done. |
| `@Q` | A question for Claude | Answer in chat, discuss, then **replace** the `@Q` with a permanent comment written for a future reader. |
| `@ASSUMPTION` | Something taken as true without confirming | Check whether it still holds. If it does and it's load-bearing, make it a comment or an assertion. If it doesn't, report it as a bug. |

**Rules:**
- Never act on a `@TODO` with more than one valid reading without confirming.
- Never leave a resolved `@Q` in place.
- A replacement comment explains why the code is as it is — it never references the conversation.
- A `@TODO` that turns out to be a feature becomes a spec, not a code edit.

---

## Session Start Checklist

1. Read this file fully
2. Read `docs/CONSTITUTION.md`
3. Read the active feature's `spec.md`, `plan.md`, `tasks.md` if one is in progress
4. State your understanding of the current state and what's next — and flag anything in these
   docs that contradicts what you see in the repo
5. Wait for confirmation before writing code
