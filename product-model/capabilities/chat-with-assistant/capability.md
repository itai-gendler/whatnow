---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/agent/agent.go#Agent.Send
- kind: code
  role: implementation
  target: internal/agent/tools.go
- kind: code
  role: implementation
  target: internal/agent/instructions.go
- kind: code
  role: implementation
  target: internal/httpapi/chat.go
- kind: code
  role: implementation
  target: web/src/lib/components/ChatDock.svelte
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.send
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Chat with the assistant

Talk to the assistant in the chat dock, or in the terminal: "push the dentist to Thursday",
"break this report into tiny steps". The main model replies in the voice set in Assistant style and
acts directly, without asking first, on tasks, events, blockers, the pace and the plan. Everything one
reply does is one change with its own Undo. Replies stream into every open chat as they are written,
and each date starts a fresh chat.
