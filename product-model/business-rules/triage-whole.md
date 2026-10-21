---
appliesTo:
- type: capability
  id: start-day
- type: capability
  id: wrap-up-day
references:
- kind: code
  role: implementation
  target: internal/planner/close.go#checkStale
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.applyTriage
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# A triage applies whole or not at all

The roll over, push and drop choices of a morning reconcile or a wrap-up apply together as one change.
A choice for a task that is no longer unfinished, such as one finished in another tab, refuses the
whole start or wrap-up before anything is written. A push without a date goes to tomorrow, and a task
without a choice rolls over.

## Rationale

Applying a stale choice would turn a completion into a drop.
