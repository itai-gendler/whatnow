---
appliesTo:
- type: context
  context:
    place: web
- type: context
  context:
    place: tui
references:
- kind: code
  role: implementation
  target: internal/app/app.go
- kind: code
  role: implementation
  target: internal/tui/model.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-tui-design.md
---

# The web UI and the terminal stay in step

Either UI, or both at once, can be used on the same day. A change made in one shows in the other: at
once when they share one running whatnow; otherwise the terminal reloads every five seconds and the
web catches up when its window regains focus.
