---
domain: today
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/planner/move.go#Planner.Move
- kind: code
  role: implementation
  target: internal/httpapi/days.go#Server.moveTask
- kind: code
  role: implementation
  target: web/src/lib/components/TaskCard.svelte#move
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Move a task to Unplanned

Take a task out of today's plan without dropping it: Move › Unplanned on a planned task on
Today. Like any move by hand, it saves a new plan version with no model call and no undo, and later
replans weigh it. The task stays open in the unplanned tray.
