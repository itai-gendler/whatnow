---
domain: integrations
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.SetEnabled
- kind: code
  role: implementation
  target: web/src/lib/components/IntegrationCard.svelte#toggle
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Turn off an integration

Turn an integration off with the switch on its card. Its saved fields, calendars and skipped list stay,
so turning it on again needs no setup.
