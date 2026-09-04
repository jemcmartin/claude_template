---
description: Sweep the repo for @TODO, @Q, and @ASSUMPTION annotations and resolve them
argument-hint: "[path to limit the sweep]"
---

Find and act on inline annotations. Limit the sweep to `$1` if given, otherwise the whole repo
excluding build output and dependencies.

Search for `@TODO`, `@Q`, and `@ASSUMPTION` in source, docs, and config.

## First, list what you found

Group by file, with the line reference and the text. Do not act until the user has seen the
list — a sweep that starts editing immediately is impossible to review.

## Then work through them

**`@TODO`** — an action for you.
Execute it if the intent is unambiguous and the change is contained. If it needs a decision, is
larger than a small contained change, or could be read two ways, **ask first**. Remove the
annotation once the action is complete.

**`@Q`** — a question for you.
Answer it in chat and discuss. Once resolved, **replace** the `@Q` with a permanent comment
that helps a future reader — explaining why the code is the way it is, not narrating that a
conversation happened. Never leave a resolved `@Q` in place.

**`@ASSUMPTION`** — something taken as true without confirmation.
Check whether it still holds. If it does and it's load-bearing, turn it into a comment or an
assertion. If it doesn't, that's a bug — report it before changing anything.

## Anything too large

A `@TODO` that turns out to be a feature is not a code edit. Say so, and offer to write it up
as a spec instead.

## Finally

Report: resolved, needs-a-decision-from-you, and escalated-to-a-spec. Confirm none remain in
code you touched during the current feature.
