---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User opens Today
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Day is wrapped
  kind: condition
  entities:
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product shows the day's-done card with the win line, the Day's reflection and the note for tomorrow
    in place of the tiers
  kind: product
  entities:
  - {entity: day, effect: reads, facts: [Reflection, Note for tomorrow]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# See a wrapped day

## Trigger

The person opens Today after wrapping up the day.

## Outcome

Today shows the day's-done card. What now and Wrap up are gone; capture, chat and the tray keep working, and anything captured waits for the morning.
