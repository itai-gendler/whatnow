---
appliesTo:
- type: capability
  id: replan-day
- type: capability
  id: start-day
- type: capability
  id: ask-what-now
- type: capability
  id: move-task-to-tier
- type: capability
  id: move-task-to-unplanned
references:
- kind: code
  role: implementation
  target: internal/facts/facts.go#Eligible
- kind: code
  role: implementation
  target: internal/planner/plan.go#checkPlan
- kind: code
  role: implementation
  target: internal/planner/whatnow.go#checkPick
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Only eligible tasks are planned or picked

A task is eligible when it is open, not deleted, and not put off until after today. Plans, What now
and the unplanned tray draw on eligible tasks only. A plan that names an ineligible or unknown task, a
task twice, or a tier other than must, should and could is sent back to the model once with the
problems, and a pick that names an ineligible task the same way.
