---
appliesTo:
- type: capability
  id: chat-with-assistant
- type: capability
  id: replan-day
- type: capability
  id: ask-what-now
- type: entity
  id: settings
  facts:
  - Assistant style
references:
- kind: code
  role: implementation
  target: internal/prompt/prompt.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Assistant style changes how the assistant sounds, never what it does

Every prompt puts whatnow's own instructions first, then Assistant style under a heading that limits
it to tone and manner, then About me, then the live context. About me shapes how plans weigh each task;
style shapes only the voice.
