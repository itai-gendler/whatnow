---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Drop on an open Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product marks the Task dropped
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, from: Open, to: Dropped, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Let a task go from its menu

## Trigger

The person decides a task no longer matters.

## Outcome

The task is dropped and gone from today, and Undo is offered.

## Edge cases

- Dropping a task in the must tier makes the Product replan the day.
