---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskEditor.svelte
- kind: code
  role: implementation
  target: web/src/lib/taskForm.ts#fieldsFrom
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.CreateTask
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Add a task

Add a task through the task form, with its fields set by hand. A task added this way never goes
through tidy-up, and it waits in the unplanned tray until the next replan, unless it is due today. Blockers picked before
saving are added once the task exists.
