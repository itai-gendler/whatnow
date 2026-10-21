---
appliesTo:
- type: capability
  id: replan-day
- type: capability
  id: start-day
- type: capability
  id: ask-what-now
- type: capability
  id: wrap-up-day
references:
- kind: code
  role: implementation
  target: internal/planner/plan.go#fallbackPlan
- kind: code
  role: implementation
  target: internal/planner/whatnow.go#Planner.WhatNow
- kind: code
  role: implementation
  target: internal/planner/planner.go#fallbackNote
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# When the model can't answer, code sorts by due date

If no provider is set up, the model fails, takes over a minute, or is rejected twice, code answers
instead. A rough plan puts tasks due today or overdue in must, tasks due later in should by due date,
and undated tasks in could by age. A rough pick is the first unblocked task in that order. Both say
they were made this way; triage suggestions made this way are all roll over.

## Rationale

This is the one deliberate exception to the model making every judgment, so a bad model day still
gives the person something valid.
