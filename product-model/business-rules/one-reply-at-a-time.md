---
appliesTo:
- type: capability
  id: chat-with-assistant
- type: entity
  id: chat-message
  effect: creates
references:
- kind: code
  role: implementation
  target: internal/agent/agent.go#Agent.Send
- kind: code
  role: implementation
  target: internal/httpapi/chat.go#Server.chat
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Chat answers one message at a time

While a reply is being written, another message is turned away; it can be sent once the reply is
done. A reply that has started is always finished, even if the page is
closed. One message is at most 4000 characters.
