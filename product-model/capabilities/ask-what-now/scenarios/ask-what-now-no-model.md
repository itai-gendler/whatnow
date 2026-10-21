---
kind: edge
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
- text: No provider is set up, or the main model fails
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product picks the first unblocked eligible Task, due today or overdue first, then due later, then undated,
    and says it is sorted by due date
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Due]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Get a rough pick without the model

## Trigger

The person asks What now? while no provider is set up, or the model fails or takes over a minute.

## Outcome

The first unblocked task in due-date order is shown, with a note saying code picked it.
