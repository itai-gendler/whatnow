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
  target: internal/service/tasks.go#Service.PushTask
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.PushCounts
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.act
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Push a task

Put an open task off with Push to tomorrow, on the web or in the terminal. A push sets the
task's not-before date and is counted, because a task pushed again and again says something about it.
The task leaves today's tiers at once.
