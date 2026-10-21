---
entities:
  - entity: chat-message
    shows: [From, Text]
    collects: [Text]
references:
  - kind: code
    role: implementation
    target: internal/tui/model.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-tui-design.md
---

# Chat

The terminal's chat pane, beside the list on a wide terminal or in its place on a narrow one, where
replies stream in as they are written.
