---
appliesTo:
- type: capability
  id: add-blocker
- type: capability
  id: capture-note
- type: entity
  id: blocker
  effect: creates
references:
- kind: code
  role: implementation
  target: internal/service/blockers.go#Service.AddBlocker
- kind: code
  role: implementation
  target: internal/service/blockers.go#waitsOn
- kind: code
  role: implementation
  target: internal/facts/facts.go#Compute
---

# A task never waits on itself

A blocker is refused when the task would wait on itself, directly or through other tasks, since every
task in such a loop would stay blocked for good. Only an open blocking task holds its task back.
