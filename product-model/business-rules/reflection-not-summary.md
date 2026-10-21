---
appliesTo:
- type: capability
  id: wrap-up-day
- type: capability
  id: view-today
references:
- kind: code
  role: implementation
  target: internal/planner/reflection.go
- kind: code
  role: implementation
  target: internal/domain/domain.go#Day
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-reflection-design.md
---

# The person reads the reflection, never the summary

Wrap-up writes two texts. The summary is the planner's plain notes, which later plans and chat read.
The reflection is written from it, to the person, in the voice set in Assistant style, and is what
Goodnight and the day's-done card show.
