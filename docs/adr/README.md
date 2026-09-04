# Architecture Decision Records

An ADR captures **one decision that is expensive to reverse**, the context that forced it, and
what it cost. It is written once, at the moment of deciding, and then left alone.

## When to write one

Write an ADR when a choice:

- is hard or expensive to undo later (database, auth model, deployment target, framework), **or**
- rules out an option a future reader would otherwise reach for, **or**
- looks wrong without its context ("why on earth is this synchronous?").

Do **not** write one for a choice scoped to a single feature — that belongs in the feature's
`plan.md` under *Decisions*. Do not write one for something already stated in
[CONSTITUTION.md](../CONSTITUTION.md).

## How

1. Copy `ADR_TEMPLATE.md` to `NNNN-short-slug.md` — next number, zero-padded, never reused.
2. Fill it in while the reasoning is fresh, including the options you rejected.
3. Add a row to the index below and a line to the *Architecture Decisions* table in `CLAUDE.md`.

## Lifecycle

ADRs are immutable once `Accepted`. To change a decision, write a **new** ADR that supersedes the
old one, then set the old one's status to `Superseded by NNNN`. Never edit history — the trail of
"we tried X, it failed because Y" is the most valuable part of the record.

## Index

| # | Title | Status | Date |
|---|---|---|---|
| <!-- 0001 --> | | | |
