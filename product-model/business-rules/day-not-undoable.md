---
appliesTo:
- type: capability
  id: start-day
- type: capability
  id: wrap-up-day
- type: capability
  id: undo-change
references:
- kind: code
  role: implementation
  target: internal/service/days.go#Service.StartDay
- kind: code
  role: implementation
  target: internal/planner/today.go#Planner.StartDay
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Starting and wrapping a day can't be undone

A day starts once: a second start of a day with a plan is refused. Starting a day and wrapping it are
not changes, so no Undo reaches them; a triage applied while starting or wrapping is a change of its
own. A start interrupted before its first plan was saved can be finished, keeping the pace chosen
first.

## Rationale

Undoing a start would orphan the day's plans.
