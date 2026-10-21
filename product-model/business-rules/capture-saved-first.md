---
appliesTo:
- type: capability
  id: capture-note
- type: capability
  id: start-day
references:
- kind: code
  role: implementation
  target: internal/httpapi/tasks.go#Server.createTask
- kind: code
  role: implementation
  target: internal/httpapi/days.go#Server.captureDump
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go#Runner.Enqueue
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# A note is saved before any model sees it

Whatever the person captures, in the capture box, the terminal or the morning's brain dump, is saved as
an open task in their own words at once. Tidy-up runs only afterwards, so a missing key, a failing
model or a slow one never loses a thought.

## Rationale

Capture is the one thing that must work on a bad day; the raw task stays fully usable as it is.
