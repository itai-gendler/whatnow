---
appliesTo:
- type: capability
  id: wrap-up-day
- type: capability
  id: start-day
references:
- kind: code
  role: implementation
  target: internal/planner/review.go#Planner.outcome
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Wrap-up reviews only the plan's unfinished tasks

An unfinished task is one in the day's latest plan that is still open and not pushed past today.
Tasks in the unplanned tray aren't reviewed; they wait for the morning.
