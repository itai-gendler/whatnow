---
references:
  - kind: code
    role: implementation
    target: internal/service/service.go#NewBatch
  - kind: code
    role: implementation
    target: internal/service/undo.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Change

One undoable set of edits: one action of the person's, one assistant reply, one tidy-up of a captured
note, or one ritual's triage. The person is offered Undo right after a change, or on the chat reply that made it.

## Information kept

- **Made by** — the person, a chat reply, tidy-up, or a ritual's triage
- **What changed** — each task, event, blocker or pace it touched, as it was before and after

## States

### Applied

The edits are in place.

### Undone

Every edit in it was taken back, newest first.
