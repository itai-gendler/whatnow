---
domain: integrations
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Unskip
- kind: code
  role: implementation
  target: web/src/lib/components/IntegrationCard.svelte#unskip
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Bring back a skipped item

Take a meeting series, ticket or pull request off an integration's skipped list with "bring back" on
its settings card. The next pull brings it in again.
