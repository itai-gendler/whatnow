---
type: cli
actors: [user]
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-tui-design.md
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-07-whatnow-tui-morning-design.md
  - kind: code
    role: implementation
    target: internal/tui/model.go
---

# Terminal UI

The terminal companion that running whatnow opens, meant to sit in a spare pane all day. It does the Good
morning ritual, today's list, What now, pace, undo, quick add and chat, and serves the web UI too when no
server is running. It reloads every few seconds, so changes made in the browser show up in it.
