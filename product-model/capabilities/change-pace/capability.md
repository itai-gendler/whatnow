---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: web/src/lib/components/Header.svelte#setPace
- kind: code
  role: implementation
  target: internal/service/days.go#Service.SetPace
- kind: code
  role: implementation
  target: internal/tui/actions.go#Model.shiftPace
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Change pace

Say how much the person has in them: one of five levels, from running on fumes to go hard. Set in the
morning, then changed any time on Today, or in the terminal one step at
a time. A pace change replans the day, and undoing it replans again.
