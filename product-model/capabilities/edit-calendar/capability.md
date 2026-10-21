---
domain: integrations
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#listRows
- kind: code
  role: implementation
  target: web/src/lib/components/IntegrationCard.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Edit a calendar

Rename a calendar, or give it a new secret address, on the Google Calendar card and Save. A blank
address keeps the one saved, so a rename never needs the address again.
