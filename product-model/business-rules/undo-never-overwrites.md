---
appliesTo:
- type: capability
  id: undo-change
- type: capability
  id: chat-with-assistant
references:
- kind: code
  role: implementation
  target: internal/service/undo.go#Service.Undo
- kind: code
  role: implementation
  target: internal/service/undo.go#revert
---

# Undo never overwrites a later edit

An undo is refused when anything that touched the same task, event, blocker or day afterwards hasn't
been undone itself. Restoring a blocker that would now close a loop, or a meeting pulled again since,
is refused the same way. A refused undo changes nothing.
