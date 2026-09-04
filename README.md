# Spec-Driven Development Template

A repo skeleton for building long-running, complex projects with Claude Code — where the
**specification is the source of truth and the code is what falls out of it**.

You are the product owner. Claude is the engineering team. You don't need the whole end goal
up front; you discover it feature by feature. What you do need is that every feature is
*written down before it's built*, and that the writing stays true afterwards.

**Recommended tool:** the Claude Code extension for VS Code (see [Setup](#setup)).

---

## Why spec-driven, and why it matters more with an AI

Claude can produce a plausible implementation of almost anything you describe. That's exactly
the problem: **plausible is not the same as correct**, and on a long project the gap compounds.
Ambiguity in a prompt doesn't stop the work — it gets silently resolved into a guess, and the
guess becomes code, and the code becomes the thing everything else is built on.

Spec-driven development closes that gap with three habits:

- **Separate WHAT from HOW.** The spec says what must be true and why. The plan says how. Mixing
  them means you can't review either — you end up arguing about a library when you haven't
  agreed what the feature does.
- **Make ambiguity loud.** Anything underspecified gets marked `[NEEDS CLARIFICATION]` instead
  of guessed. A question costs you thirty seconds; a wrong guess costs a day.
- **Make everything traceable.** Requirements, acceptance criteria, tasks, and tests are linked
  by stable IDs. That chain is how you can tell — mechanically, not by vibes — whether the
  thing that got built is the thing you asked for.

And a fourth reason specific to Claude: **sessions have no memory.** The repo is the memory.
Documents that stay accurate are the difference between a session that resumes in one minute
and one that spends twenty re-deriving what's going on.

---

## The Pipeline

```
  /kickoff ──────► CLAUDE.md, CONSTITUTION.md, GLOSSARY.md populated by interview
                   (once, at project start)

  ┌──────────────────── per feature ─────────────────────┐

  /specify  ─► spec.md      WHAT & WHY. No tech. Gaps marked, not guessed.
      │                                                     ▲
      ▼                                                     │
  /clarify  ─► open questions resolved, spec Approved   ─────┘ gate: no markers left

  /plan     ─► plan.md      HOW. Constitution check, decisions, risks, test strategy.
      │                                                     ▲
      ▼                                                     │
  /tasks    ─► tasks.md     Ordered, verifiable units  ─────┘ gate: every AC covered

  /implement ─► code + tests, tasks ticked as they land

  /verify   ─► adversarial check of every AC. Finds what's missing.
      │                                                     ▲
      ▼                                                     │
  /ship     ─► CLAUDE.md, FEATURE_LOG.md, ARCHITECTURE, ADRs brought back in step

  └──────────────────────────────────────────────────────┘
```

Each arrow is a gate. **You** decide when to pass one — Claude stops and asks. The gates exist
because a wrong sentence in a spec costs a minute to fix, and the same mistake discovered in
merged code costs a day.

You can skip gates on small work. That's your call to make, deliberately — not Claude's to make
quietly.

---

## What's in Here

| Path | Purpose | Who maintains it |
|---|---|---|
| `CLAUDE.md` | Project brain. Loaded every session. Short and true. | Claude writes, you correct |
| `docs/CONSTITUTION.md` | Non-negotiable rules. Gates every plan. | You own it; Claude proposes amendments |
| `docs/ARCHITECTURE.md` | System shape, invariants, known debt. | Claude updates at `/ship` |
| `docs/GLOSSARY.md` | Domain vocabulary used by specs, code, and UI alike. | Claude appends, you arbitrate |
| `docs/adr/` | Architecture decision records — one per hard-to-reverse choice. | Claude drafts, you accept |
| `docs/features/` | One folder per feature: `spec.md`, `plan.md`, `tasks.md`, `assets/`. | Claude creates, you review |
| `docs/features/_templates/` | The three phase templates. Leave as-is. | Nobody |
| `FEATURE_LOG.md` | Archive of what shipped and why. | Claude appends at `/ship` |
| `.claude/commands/` | The pipeline commands above. | Tune once you know your project |

Four documents are *living* — `CLAUDE.md`, `ARCHITECTURE.md`, `GLOSSARY.md`, `FEATURE_LOG.md`.
They describe the project as it is now. **Stale is worse than absent**: an empty section is
honest, a wrong one silently misleads every session that follows.

---

## Setup

### Install Claude Code for VS Code

1. Extensions panel (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search **"Claude Code"** — install the one published by **Anthropic** (verified publisher
   badge). There are unofficial lookalikes; check the publisher.
3. A Spark icon appears in the sidebar — click it to open the panel
4. Sign in when prompted

### Why in-repo, not claude.ai chat

Running inside the repo is what makes this template work:

- Claude reads `CLAUDE.md` and the specs from disk — no copy-pasting, no drift
- Claude creates and updates the spec/plan/task files as part of the loop, so the documents
  can't fall behind the code
- Changes arrive as **inline diffs** you accept or reject per hunk — your main quality gate
- `@mention` any file directly in a prompt (`@docs/features/FEAT_001_login/spec.md`)
- The `/` commands in `.claude/commands/` are available as slash commands

---

## Starting a New Project

**1. Copy this repo** and open the folder in VS Code. Don't fill anything in yet.

**2. Run `/kickoff`.** Claude interviews you — one area at a time — about what you're building,
who it's for, your stack, your constraints, and how strictly you want to work. Then it writes
`CLAUDE.md`, `docs/CONSTITUTION.md`, and `docs/GLOSSARY.md` for you.

> **You don't need all the answers.** "I haven't decided" is a valid response — it gets recorded
> as an open decision rather than quietly resolved into a choice you never made.

**3. Review what it wrote.** Correct it directly. Pay closest attention to the constitution —
those rules gate every feature after this.

**4. Start your first feature.** New session, then `/specify <your idea>`.

**5. Every session after that: `/prime`.** It loads the brain, the constitution, and the active
feature, then tells you where things stand and what's waiting on you.

---

## Running a Feature

Your request can be a sentence (*"add a login page"*), a paragraph, a mockup image, or a vague
direction (*"users should be able to save things somehow"*). Claude turns it into a spec and
asks what it needs.

```
/specify Users should be able to sign in with Google
/clarify FEAT_001          ← answer the open questions
/plan FEAT_001             ← approve the approach
/tasks FEAT_001
/implement FEAT_001        ← repeat until tasks are done
/verify FEAT_001
/ship FEAT_001
```

**Before Claude builds anything**, make sure you've agreed:

- [ ] Acceptance criteria are written and feel right to you
- [ ] The approach is one you'd defend
- [ ] Blocking action items are known (they don't have to be *done* yet)
- [ ] Out-of-scope is written down

Acceptance criteria are the part people skip and the part that matters most — they're what makes
tests meaningful and what `/verify` checks against. A vague criterion produces a vague test that
passes whatever you build.

---

## The Constitution

`docs/CONSTITUTION.md` holds the rules Claude must plan *within*. Every plan runs a compliance
check against it, and a violation stops the plan rather than getting logged and passed over.

It ships with eight starter articles — spec before code, no silent guessing, testable criteria,
tests from spec, simplicity, recorded decisions, current docs, bounded scope. During `/kickoff`
you'll set the testing strictness and add rules specific to your project ("money is stored in
integer minor units", "no PII leaves the EU").

Amendments are versioned and dated. Claude will not change it mid-feature to make a plan fit —
it asks you, because that's a product decision, not an engineering one.

---

## Inline Annotations

Leave these anywhere in code or docs; `/annotations` sweeps and resolves them, and `/verify`
flags any left behind.

```ts
// @TODO add input validation here
// @Q why does this need to be async if we never await it?
// @ASSUMPTION the upstream API always returns UTC timestamps
```

| | What Claude does |
|---|---|
| `@TODO` | Executes it if the intent is unambiguous and contained; otherwise asks first |
| `@Q` | Answers in chat, then **replaces** it with a permanent comment for a future reader |
| `@ASSUMPTION` | Checks whether it still holds — if it doesn't, that's a bug report, not a fix |

---

## Working Well With This

**On mockups.** Paste images straight into the chat. Claude saves them to the feature's
`assets/` and writes its interpretation into the spec. **Always confirm that interpretation** —
a misread mockup is the single most common cause of rework.

**On pushing back.** Disagree with the approach in the plan, before the tasks exist. That's what
the *Alternatives considered* table is for, and it stops the same debate recurring in three
months.

**On pivoting.** Changing direction is fine. Say what changed and why; Claude updates the spec's
change log and `CLAUDE.md`. These documents track current intent, never original intent.

**On scope creep.** New ideas mid-feature become new specs, not additions to the current one.
This is the discipline that keeps a long project finishable.

**On diffs.** Review every hunk before accepting. You can edit Claude's proposed change in the
diff view before it lands.

**On going sideways.** Double-press `ESC` to rewind to an earlier message and roll the code back
to that exact state — better than manually undoing.

**On long features.** `tasks.md` has a *Session Notes* log. A new session reads it and picks up
where the last one stopped, instead of re-deriving the situation from the diff.

**On honesty.** If tests fail, you want to hear it. The commands are written to report actual
output and name what was skipped. Treat "everything looks good" with no evidence as a finding
in itself.

---

## Adapting the Template

This is a starting point, not a cage. Once your project has a shape:

- Add project-specific articles to the constitution as you learn what keeps biting you
- Trim spec sections your project never uses — a template nobody fills in honestly is worse
  than a shorter one everybody does
- Adjust the commands in `.claude/commands/` to match your stack (test commands, lint, deploy)
- Add `.claude/settings.json` permissions for the commands you run constantly, so you stop
  approving the same thing

The one thing worth not loosening: **the gates**. They're the whole mechanism.
