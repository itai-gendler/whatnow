---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User asks What now?
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: No eligible Task is free of open blockers
  kind: condition
  entities:
  - {entity: task, effect: reads, facts: []}
  - {entity: blocker, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product says there is nothing to do right now
  kind: product
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Nothing is free to start

## Trigger

The person asks What now? when no eligible task is free to start.

## Outcome

A quiet note says "Nothing to do right now. Enjoy it." instead of an error.
