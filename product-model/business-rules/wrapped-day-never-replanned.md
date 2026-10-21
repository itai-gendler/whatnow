---
appliesTo:
- type: capability
  id: replan-day
- type: capability
  id: move-task-to-tier
- type: capability
  id: move-task-to-unplanned
- type: capability
  id: chat-with-assistant
references:
- kind: code
  role: implementation
  target: internal/planner/plan.go#Planner.Replan
- kind: code
  role: implementation
  target: internal/planner/move.go#Planner.Move
- kind: code
  role: implementation
  target: internal/planner/triggers.go#Planner.reasons
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# A wrapped day is never replanned

Once a day is wrapped, nothing makes a new plan version for it: no replan, no automatic trigger, no
assistant and no move by hand.
