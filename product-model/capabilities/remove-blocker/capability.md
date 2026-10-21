---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskEditor.svelte#removeBlocker
- kind: code
  role: implementation
  target: internal/service/blockers.go#Service.RemoveBlocker
---

# Remove a blocker

Take a blocker off a task with ✕ beside it under "Blocked by" in the task sheet. Each removal is its
own undoable step.
