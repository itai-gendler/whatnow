---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/TaskEditor.svelte#addBlocker
- kind: code
  role: implementation
  target: internal/service/blockers.go#Service.AddBlocker
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Add a blocker

Record that a task can't start until another open task is finished, from "Add a blocker…" in the
task sheet. Each blocker added is its own undoable step. A task never waits on itself, directly or
through other tasks.
