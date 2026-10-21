---
domain: today
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/planner/plan.go#Planner.Replan
- kind: code
  role: implementation
  target: internal/planner/triggers.go
- kind: code
  role: implementation
  target: internal/planner/instructions.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/+page.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Replan the day

Make a fresh version of today's plan. The plan holds still until something warrants a change: the
Replan button in the unplanned tray, a pace change, a task becoming due today, a must dropped or
deleted, a blocker added or removed on a must, or the assistant deciding the day has changed. New tasks
otherwise wait in the tray. A wrapped day is never replanned.
