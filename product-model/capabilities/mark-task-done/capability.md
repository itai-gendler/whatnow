---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskCard.svelte
- kind: code
  role: implementation
  target: web/src/lib/components/WhatNow.svelte
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.SetTaskStatus
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.act
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Mark a task done

Mark an open task done: its checkbox, Done on a What now pick, or the terminal's list.
It leaves today's tiers at once and joins Done today. Finishing a must doesn't replan.
