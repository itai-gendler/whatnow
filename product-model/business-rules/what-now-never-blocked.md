---
appliesTo:
- type: capability
  id: ask-what-now
- type: capability
  id: pass-on-pick
references:
- kind: code
  role: implementation
  target: internal/planner/whatnow.go#checkPick
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# What now never picks a blocked task or the one just passed on

A pick must be free to start: no open task it waits on. After "not this one", the task passed on is
left out of that answer only; the next What now may pick it again.
