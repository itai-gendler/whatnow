---
entities:
  - entity: google-calendar-integration
    shows: [On]
  - entity: calendar
    shows: [Name]
    collects: [Name, Secret address]
  - entity: jira-integration
    shows: [On, Address, Search (JQL)]
    collects: [Address, Personal access token, Search (JQL)]
  - entity: review-queue-integration
    shows: [On, Address, Minimum score]
    collects: [Address, Minimum score]
  - entity: skipped-item
    shows: [Title]
  - entity: event
    shows: [Title, Starts]
  - entity: task
    shows: [Title]
entryPoints:
  - web: /settings/integrations
references:
  - kind: code
    role: implementation
    target: web/src/routes/settings/integrations/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/IntegrationCard.svelte
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Integrations

The Integrations section of Settings: one card each for Google Calendar, Jira and Review Queue, with
its on switch, its fields, its skipped items with "bring back", and a pull whose results show on the
card.
