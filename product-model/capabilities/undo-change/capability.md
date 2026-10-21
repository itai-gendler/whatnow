---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/service/undo.go#Service.Undo
- kind: code
  role: implementation
  target: internal/httpapi/tasks.go#Server.undo
- kind: code
  role: implementation
  target: web/src/lib/toasts.svelte.ts
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.undo
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Undo a change

Take back one change whole: the Undo offered after it, Undo on a chat reply, or undo in the terminal for the
person's own last change there. Every edit to tasks, events, blockers and the pace is part of exactly
one change. Starting a day, wrapping it, moving a task by hand and making a plan are not changes and
can't be undone. Undo never overwrites anything edited since.
