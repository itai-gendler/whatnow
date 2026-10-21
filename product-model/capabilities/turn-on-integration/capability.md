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

# Turn on an integration

Turn an integration on with the switch on its card. The switch saves at once, apart from the card's
fields, and opens the card. An integration pulls only while it is on and its required fields are
saved.
