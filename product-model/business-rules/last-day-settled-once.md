---
appliesTo:
- type: capability
  id: start-day
- type: entity
  id: day
  effect: changes
  to: Wrapped
references:
- kind: code
  role: implementation
  target: internal/planner/review.go#Planner.MorningReview
- kind: code
  role: implementation
  target: internal/planner/review.go#Planner.unwrapped
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.Close
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-reflection-design.md
---

# Only the last day before today is settled in the morning

If the last day started before today was never wrapped up, the next morning shows its unfinished
tasks to settle and wraps it, writing its summary but no reflection. However many days were skipped,
only that last one is settled.
