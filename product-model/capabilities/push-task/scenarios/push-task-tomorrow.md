---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Push to tomorrow on an open Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product sets the Task's not-before date to tomorrow and counts the push
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Not before, Times pushed]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Task leaves today's tiers and the tray until tomorrow
  kind: condition
  entities:
  - {entity: task, effect: reads, facts: [Not before]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Push a task to tomorrow

## Trigger

The person won't get to a task today.

## Outcome

The task comes back tomorrow, its push count is one higher, and Undo is offered.

## Edge cases

- Plans see the push count, so a task pushed many times may be suggested for breaking down rather than as a must again.
