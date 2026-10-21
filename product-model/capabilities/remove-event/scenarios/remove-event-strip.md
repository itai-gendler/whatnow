---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses × on an Event on the day strip
  kind: actor
  actor: user
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
- text: The Product removes the Event
  kind: product
  actor: user
  entities:
  - {entity: event, effect: removes}
  contexts:
    web:
      place: web::today
---

# Remove an event from the day strip

## Trigger

A meeting was cancelled, or was never real.

## Outcome

The event is gone from the strip and from planning's free time, and Undo is offered.
