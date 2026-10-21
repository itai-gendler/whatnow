---
appliesTo:
- type: capability
  id: replan-day
- type: capability
  id: change-pace
- type: capability
  id: drop-task
- type: capability
  id: capture-note
- type: capability
  id: add-task
- type: capability
  id: add-tickets
references:
- kind: code
  role: implementation
  target: internal/planner/triggers.go#replanReasons
- kind: code
  role: implementation
  target: internal/planner/triggers.go#Planner.Run
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# The plan changes only when something warrants it

A new plan version is made when the day starts, the pace changes, a task becomes due today, a must is
dropped or deleted, a blocker on a must is added or removed, the assistant replans, the person chooses
Replan, or a task is moved by hand. Undoing such a change replans too. Every other new task waits in
the unplanned tray, and finishing a must just marks it done.

## Rationale

A plan that holds still is easier to trust, while What now always reasons over the current state.
