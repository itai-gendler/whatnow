---
appliesTo:
- type: capability
  id: chat-with-assistant
- type: capability
  id: undo-change
references:
- kind: code
  role: implementation
  target: internal/agent/agent.go#Agent.Send
- kind: code
  role: implementation
  target: internal/agent/tools.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Everything one reply does is one change

All the assistant's actions in one reply are one change, undone whole by the reply's Undo. If an action
fails partway, the earlier ones stay done and stay in that change. A reply whose actions all failed has
no Undo. "Undo that" in chat takes back the latest change by the assistant or tidy-up, never the
current reply's own.
