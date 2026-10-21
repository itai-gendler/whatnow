---
appliesTo:
- type: capability
  id: move-task-to-tier
- type: capability
  id: move-task-to-unplanned
- type: capability
  id: replan-day
references:
- kind: code
  role: implementation
  target: internal/planner/move.go#Planner.Move
- kind: code
  role: implementation
  target: internal/planner/planner.go
- kind: code
  role: implementation
  target: internal/planner/instructions.go
---

# Later replans weigh a move made by hand

A task moved by hand gets the rationale "You moved this here.", and every later replan that day is
told what was moved, from where and to where. The model weighs those moves heavily but may still move
the task when the day has changed since.
