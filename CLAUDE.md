# CLAUDE.md — Project Brain

> **This file starts blank. Don't fill it in manually.**
> Use the kickoff prompt in README.md to have Claude interview you and populate this file through conversation.
> Once populated, this becomes the source of truth for the project — Claude reads it at the start of every session.
> Keep it updated. It should always reflect the current state of the build.

---

## Project Overview

**What is this?**
<!-- One paragraph. What does this app do, who is it for, what problem does it solve? -->

**What does "done" look like?**
<!-- Describe the end state you're working toward, even if loosely. -->

---

## Tech Stack

| Layer | Choice | Why |
|---|---|---|
| Frontend | | |
| Backend | | |
| Database | | |
| Auth | | |
| Hosting | | |
| Testing | | |

**Key constraints:**
<!-- Things Claude should never change or work around. e.g. "Always use environment variables for secrets", "No third-party UI libraries" -->

---

## Current State

**What's been built:**
<!-- Brief summary of what exists and works today. Update after every feature. -->

**What's in progress:**
<!-- Feature currently being worked on. Link to its feature file. -->

**What's next (rough):**
<!-- Optional loose backlog. Not a contract, just intent. -->

---

## Pending Action Items

> These are things **you** need to do before certain features can be built or tested.
> Check them off as you complete them.

- [ ] <!-- Example: Create Google OAuth client ID -->
- [ ] <!-- Example: Set up hosting environment -->

---

## Architecture Decisions

> A running log of key decisions and why they were made.
> Claude should not reverse these without discussion.

| Decision | Rationale | Date |
|---|---|---|
| | | |

---

## How to Run This Project

```bash
# Install dependencies
# fill in

# Run locally
# fill in

# Run tests
# fill in
```

---

## Code Annotation Conventions

> These decorators can appear in any file — source code, feature docs, or config. Claude scans for them during code review and acts on them in place.

| Decorator | Intent | Claude's behavior |
|---|---|---|
| `@TODO` | An action Claude should take | Execute the action if intent is clear. If ambiguous, or if a decision is required, prompt the user before acting. |
| `@Q` | A question for Claude to answer | Answer in chat and discuss. Once resolved, replace the `@Q` comment with a permanent clarifying comment. |

**Rules:**
- Never act on an `@TODO` that could have multiple valid interpretations without confirming first.
- Never leave an `@Q` in place after the question is resolved — always replace it.
- When replacing `@Q`, write a comment that would help a future reader, not one that references the conversation.

---

## Session Start Checklist

When beginning a new session, Claude should:
1. Read this file fully
2. Read the current in-progress feature file if one exists
3. Confirm current state understanding before writing any code
