---
domain: integrations
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Save
- kind: code
  role: implementation
  target: web/src/lib/components/IntegrationCard.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Remove a calendar

Stop reading a calendar: remove beside its row on the Google Calendar card, then Save. Its secret
address is deleted from the system keychain. Its meetings already pulled stay until the next pull.
