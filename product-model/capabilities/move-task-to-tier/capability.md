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
  target: web/src/lib/components/TaskCard.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Move a task to a tier

Put a task in a tier of today's plan by hand, from another tier or from the unplanned tray: Move › and
Must, Should or Could on a task on Today. It saves a new plan version with no model call and no undo. Later replans see
each move made by hand and weigh it, but can still move the task again.
