---
appliesTo:
- type: capability
  id: wrap-up-day
- type: capability
  id: start-day
references:
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.WrapUp
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.Close
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-reflection-design.md
---

# A day wraps even when its summary or reflection can't be written

A summary or reflection that fails is left empty and the day still wraps. With no summary, no
reflection is written. Both are written even if the person leaves mid-way.
