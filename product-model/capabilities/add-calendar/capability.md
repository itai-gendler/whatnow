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
  target: internal/integrations/gcal/gcal.go#Calendar.Fields
- kind: code
  role: implementation
  target: web/src/lib/components/IntegrationCard.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Add a calendar

Add a Google Calendar to read meetings from: + Add under Calendars on the Google Calendar card, a name
and the calendar's secret address in iCal format, then Save. The help line says where Google keeps the
secret address.
