---
appliesTo:
- type: capability
  id: pull-today
- type: capability
  id: pull-tickets
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Pull
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Integrations pull only when asked, and only today

Nothing is fetched in the background: a pull happens when the person pulls from the morning, a
settings card or the terminal's morning, and it covers today, in local time.

## Rationale

A calendar's feed is its whole history, often tens of megabytes.
