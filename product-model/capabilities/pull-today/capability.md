---
domain: integrations
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Pull
- kind: code
  role: implementation
  target: internal/service/sync.go#Service.SyncEvents
- kind: code
  role: implementation
  target: internal/integrations/gcal/gcal.go
- kind: code
  role: implementation
  target: web/src/lib/components/MorningIntegrations.svelte
- kind: code
  role: implementation
  target: web/src/lib/components/PullResults.svelte
- kind: code
  role: implementation
  target: internal/tui/calendar.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Pull today

Bring today's meetings in from every calendar set up in the Google Calendar integration: from the brain dump step, Pull today on its settings card, or the Calendar step of the terminal's
morning. Pulls happen only when asked and cover today only. A second pull brings today in line with the
feed: moved meetings move, cancelled ones disappear, and anything the person removed stays removed.
The pull is one change.
