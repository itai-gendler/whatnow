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
  target: internal/service/tasks.go#Service.SetTaskStatus
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.act
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Drop a task

Let an open task go without doing it with Drop, on the web or in the terminal. A dropped
task stays on All tasks under Dropped, where it can be restored. Dropping a must sets off a replan.
