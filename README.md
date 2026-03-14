# Vibe Coding Template

A process for driving high-quality iterative development with Claude — feature by feature, with architecture discussions, clear action items, and solid test coverage.

**Recommended tool:** Claude Code extension for VS Code (see [Setup](#setup) below).

---

## How This Works

You are the product owner. Claude is the engineering team. You don't need to know the full end goal upfront — you discover it feature by feature.

### The Loop

```
1. You drop a feature request
        ↓
2. Claude re-reads CLAUDE.md to anchor on the project state
        ↓
3. Claude responds with:
   - Recommended approach + reasoning (push back if you disagree)
   - Your action items as a checklist
   - Clarifying questions to sharpen test coverage
   Claude also creates a new FEAT_NNN.md file in /docs/features/ capturing all of this
        ↓
4. You react — approve, push back, answer questions, check off items
        ↓
5. Claude builds + writes tests based on agreed acceptance criteria
        ↓
6. You experience it, decide what's next
        ↓
7. Claude updates CLAUDE.md + archives feature to FEATURE_LOG.md
```

---

## Files in This Repo

| File | Purpose | Who manages it |
|---|---|---|
| `CLAUDE.md` | The living brain of the project. Claude reads this every session. | Claude writes it, you review and correct |
| `FEATURE_LOG.md` | Archive of completed features and decisions. | Claude updates when a feature is complete |
| `docs/features/FEAT_TEMPLATE.md` | Structural template Claude uses to create feature files. Don't edit this. | Leave as-is |
| `docs/features/FEAT_NNN_name.md` | One file per feature — Claude creates and fills these in response to your feature requests. | Claude creates, you review |
| `docs/features/assets/FEAT_NNN/` | Images you submit with a feature request — mockups, diagrams, screenshots. Claude saves them here and embeds them in the feature file. | Claude saves, you supply |

---

## Setup

### Install Claude Code for VS Code

1. Open VS Code and go to the Extensions panel (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search for **"Claude Code"** — install the one published by **Anthropic** (look for the verified publisher badge)
3. Once installed, a **Spark icon** will appear in your sidebar — click it to open the Claude Code panel
4. Sign in with your Anthropic account when prompted

> **Important:** There are unofficial Claude extensions in the marketplace. Make sure you install the one by Anthropic specifically.

### Why Claude Code (not claude.ai chat)

Claude Code runs inside your repo. This is what makes the template work as designed:

- Claude reads `CLAUDE.md` directly from your filesystem at the start of every session — no copy/pasting
- Claude creates and updates feature files (`FEAT_NNN.md`, `FEATURE_LOG.md`) as part of the loop
- Code changes appear as **inline diffs** in your editor — you accept or reject each change before it lands
- Claude is aware of which files you have open and what code you've highlighted, so you can ask questions about specific code without copying it into chat
- You can `@mention` any file in your repo directly in the chat prompt (e.g. `@CLAUDE.md`, `@src/app/app.component.ts`)

---

## Starting a New Project

### Step 1 — Copy the template and open it in VS Code

Copy this repo and open the folder in VS Code. Don't fill in anything yet.

### Step 2 — Have a project kickoff conversation with Claude

Open the Claude Code panel (Spark icon in sidebar) and start a new conversation (`Cmd+N` on Mac, `Ctrl+N` on Windows).

Use this prompt to kick off:

```
I'm starting a new project and I want you to help me populate CLAUDE.md.

Please read @CLAUDE.md so you understand the structure, then interview me
about my project. Ask me what you need to fill it in well — what I'm building,
who it's for, my tech preferences, any constraints I know about, and what
"done" looks like (even loosely). Ask one area at a time, not everything at once.

When we've covered enough ground, write the populated CLAUDE.md to the file.
```

Claude will ask you questions, you'll answer conversationally, and by the end
you'll have a populated CLAUDE.md written directly to your repo — without
filling in a single form field.

> **It's okay not to have all the answers.** If you don't know your full tech
> stack yet, say so. Claude will note it as a decision to make and you can
> revisit it. The goal is to capture what you *do* know and make the unknowns
> visible.

### Step 3 — Review and start your first feature

Read through the CLAUDE.md Claude produced. Make any corrections directly in
the file. Then start a new session and drop your first feature request.

**Session start prompt for all future sessions:**
```
Please read @CLAUDE.md and confirm your understanding of the project state before we begin.
```

> **Tip:** If a feature is already in progress, include it too:
> `Please read @CLAUDE.md and @docs/features/FEAT_001_login.md before we begin.`

---

## Submitting a Feature Request

Your request can be:
- A sentence: *"Add a login page"*
- A paragraph with context
- A diagram or mockup image
- A rough idea: *"I want users to be able to save things somehow"*

Claude will ask what it needs to make it concrete.

---

## Before Claude Builds Anything

Make sure you've agreed on:
- [ ] The recommended approach (or your preferred alternative)
- [ ] Your action items are known (even if not done yet)
- [ ] Acceptance criteria are written and feel right to you

Don't skip the acceptance criteria step. This is what makes tests meaningful.

---

## Tips

**On mockups:** If you submit a mockup or diagram, Claude will describe its interpretation back to you before building. Always confirm this is correct — catching a misread early saves significant rework. You can paste images directly into the Claude Code chat panel.

**On action items:** Some items (like getting an API key) block the build. Others can be done in parallel. Claude will flag which is which.

**On pivoting:** It's fine to change direction. Just tell Claude what changed and why. `CLAUDE.md` should always reflect current intent, not original intent.

**On sessions:** Claude Code has no memory between sessions. Always start with the session start prompt so Claude re-reads `CLAUDE.md`. The quality of your `CLAUDE.md` directly determines how fast Claude gets up to speed.

**On diffs:** When Claude proposes code changes, they appear as inline diffs in your editor. Review them before accepting — this is your main quality gate. You can also edit Claude's proposed changes directly in the diff view before accepting.

**On going off the rails:** If a feature session goes badly sideways, Claude Code's context rewind lets you double-press `ESC` to edit a previous message and roll code back to that exact state. Use it rather than manually undoing changes.

**On @mentions:** Use `@filename` in your prompts to give Claude direct context. For example: `@src/app/auth/login.component.ts — the button styles here don't match the mockup` is much faster than describing the file.
