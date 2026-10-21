---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/DayStrip.svelte
- kind: code
  role: implementation
  target: web/src/lib/components/PullResults.svelte#removeToday
- kind: code
  role: implementation
  target: internal/service/events.go#Service.DeleteEvent
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Remove an event

Take an event off today with × on the day strip, or with × beside a meeting in a pull's results.
A meeting pulled from Google Calendar that the person removed stays removed on later pulls. For a
recurring meeting in a pull's results, × asks whether to remove just today's or skip it for good.
