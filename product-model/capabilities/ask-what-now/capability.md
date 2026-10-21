---
domain: today
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/planner/whatnow.go#Planner.WhatNow
- kind: code
  role: implementation
  target: internal/planner/instructions.go
- kind: code
  role: implementation
  target: web/src/lib/components/WhatNow.svelte
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.whatNow
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Ask what now

Get one task to start right now, with a reason: What now? on Today or in the terminal, or a click on
an event-end nudge. The main model reasons over the current state each time: every eligible task,
planned or not, the free time before the next event, the pace and how the person feels. It never picks
a blocked task.
