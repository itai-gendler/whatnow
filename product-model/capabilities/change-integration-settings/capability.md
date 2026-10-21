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
  target: web/src/lib/components/IntegrationCard.svelte#save
- kind: code
  role: implementation
  target: internal/integrations/jira/jira.go#Jira.Fields
- kind: code
  role: implementation
  target: internal/integrations/reviewqueue/reviewqueue.go#ReviewQueue.Fields
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-15-whatnow-review-queue-design.md
---

# Change integration settings

Set an integration's fields on its card in Settings → Integrations, or in the Integrations step of
first-run setup, and save them with the card's Save. Cards render from each integration's own fields:
Google Calendar's calendars, Jira's address, token and search, Review Queue's address and minimum
score. A secret left blank keeps the one saved; secrets are kept in the system keychain and shown only
as saved.
