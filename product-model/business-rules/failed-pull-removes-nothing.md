---
appliesTo:
- type: capability-scenario
  id: pull-today-calendars
- type: capability-scenario
  id: pull-today-calendar-fails
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Pull
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# A pull with a failed calendar removes nothing

When any calendar fails, the pull still adds and moves meetings from the others but removes none,
since meetings the failed calendar would have listed can't be told from cancelled ones.
