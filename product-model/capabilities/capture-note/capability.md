---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: web/src/lib/components/Capture.svelte
- kind: code
  role: implementation
  target: internal/httpapi/tasks.go#Server.createTask
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go
- kind: code
  role: implementation
  target: internal/cleanup/instructions.go
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.capture
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Capture a note

Save whatever is on the person's mind, in their own words, and have the light model tidy it into
tasks, events and blockers in the background. The note is saved before any model sees it, so capture
works without a model, and the tidy-up is one change the person can undo. The capture box sits on
Today and during both rituals, and the terminal has its own quick add.
