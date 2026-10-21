---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User clicks an event-end nudge, as a notification or in the page
  kind: actor
  actor: user
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web
- text: The Product focuses the tab and opens Today, leaving a ritual page if need be
  kind: product
  entities: []
  contexts:
    web:
      place: web::today
- text: The main model picks one unblocked Task with a reason, and the Product shows it
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
---

# Ask what now from an event-end nudge

## Trigger

A meeting has just ended and the person clicks its nudge, "Standup's done. What now?".

## Outcome

Today opens with a fresh pick; the model ran only because of the click.

## Edge cases

- Once the day is wrapped, the click opens Today without asking.
