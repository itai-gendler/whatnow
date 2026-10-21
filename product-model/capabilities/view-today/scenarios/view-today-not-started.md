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
- text: The Product finds nothing started for today's date yet
  kind: condition
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product takes the User to Good morning, or shows the good-morning card in the terminal
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::today
---

# Open Today before the day has started

## Trigger

The person opens whatnow on a date with no started day, such as first thing in the morning.

## Outcome

The person is in Good morning on the web, or sees the good-morning card in the terminal, ready to start the day.

## Edge cases

- On the web, first-run setup comes first while setup isn't finished and no provider is saved.
- A tab left open across midnight goes to Good morning when the window regains focus and the new date has no plan.
- The terminal waits for enter rather than starting the morning on its own.
