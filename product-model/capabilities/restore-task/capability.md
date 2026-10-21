---
domain: all-tasks
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskCard.svelte#restore
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.SetTaskStatus
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Restore a task

Bring a dropped task back to open, from Restore on its card under Dropped on All tasks.
