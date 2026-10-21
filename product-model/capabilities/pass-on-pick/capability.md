---
domain: today
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/httpapi/days.go#Server.whatNow
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.AppendFeeling
- kind: code
  role: implementation
  target: internal/planner/whatnow.go#Planner.WhatNow
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.whatNow
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Pass on a pick

Say "not this one" to What now's pick, optionally with why, and get another: Not this one on the pick
card or in the terminal. The reason is added to the task's feeling, so later plans and picks read
it. The task is left out of this answer only.
