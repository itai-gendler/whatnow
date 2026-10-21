---
appliesTo:
- type: capability
  id: capture-note
- type: capability
  id: start-day
references:
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go#Runner.join
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go#Runner.openTickets
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# A note naming an open task's ticket key joins that task

When tidy-up finds a ticket key, such as FLEX1-666, that an open task already carries, it adds the
note's feeling to that task and points any blockers at it instead of making a second task; a note that
joined is removed. Only ticket keys join, and a done task's key doesn't count.

## Rationale

A looser match would need the model's judgment, and a wrong guess would quietly swallow a note. A
note about a finished ticket means the work came back.
