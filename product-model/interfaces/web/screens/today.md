---
entities:
  - entity: day
    shows: [Date, Pace, Reflection, Note for tomorrow]
  - entity: plan
    shows: [Tiers, Rough plan]
  - entity: task
    shows: [Title, Size, Energy, Feeling, Notes]
  - entity: blocker
    shows: [Blocking task]
  - entity: event
    shows: [Title, Starts, Ends]
  - entity: settings
    shows: [End of day]
  - entity: change
    shows: [What changed]
entryPoints:
  - web: /
references:
  - kind: code
    role: implementation
    target: web/src/routes/(app)/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/Header.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/TaskCard.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/DayStrip.svelte
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
---

# Today

Today's plan and everything around it: the date, the pace, a countdown to the next event, the day
strip of today's events with a now line, the capture box, the must, should and could tiers, the
unplanned tray, and Done today with the win line. Once the day is wrapped, the tiers give way to the
day's-done card with the reflection and the note for tomorrow.
