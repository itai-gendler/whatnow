---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskEditor.svelte
- kind: code
  role: implementation
  target: web/src/lib/components/EditSheet.svelte
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.UpdateTask
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Edit a task

Change a task's own facts in the task sheet: title, notes, size, energy, feeling, due date and
not-before date. The words as captured are shown but never change. Opened from a task on Today or on
All tasks.
