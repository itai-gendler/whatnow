---
singleton: true
domain: integrations
relations:
  - entity: calendar
    verb: reads
    cardinality: one-to-many
  - entity: skipped-item
    verb: skips
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: internal/integrations/gcal/gcal.go
  - kind: code
    role: implementation
    target: internal/integrations/saved.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Google Calendar integration

The Google Calendar setup: the calendars whose meetings are pulled into today, and the recurring
meetings skipped for good. It pulls only while it is on and has at least one calendar.

## Information kept

- **On** — whether it is turned on; turning it off keeps its calendars
