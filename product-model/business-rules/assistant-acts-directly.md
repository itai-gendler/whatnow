---
appliesTo:
- type: capability
  id: chat-with-assistant
- type: capability
  id: capture-note
references:
- kind: code
  role: implementation
  target: internal/agent/instructions.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# The assistant acts without asking first

When the person asks for something in chat, the assistant does it, asking only when it can't tell what
they mean. Every change it makes can be undone, so there is no confirmation step.

## Rationale

Low friction over confirmation: each extra question is a place an ADHD day stalls.
