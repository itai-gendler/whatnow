---
appliesTo:
- type: capability
  id: capture-note
- type: capability
  id: start-day
references:
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go#Runner.Clean
- kind: code
  role: implementation
  target: internal/cleanup/cleanup.go#Runner.unchanged
---

# Tidy-up never overwrites a note edited since capture

Tidy-up checks the captured task before it asks the model and again before it writes. If the person
has edited or deleted the task in between, tidy-up changes nothing and says nothing.
