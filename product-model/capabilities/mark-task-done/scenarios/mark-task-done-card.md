---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User ticks an open Task on Today
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product marks the Task done
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, from: Open, to: Done, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product counts it in the win line
  kind: product
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Tick a task off

## Trigger

The person has finished something on today's list.

## Outcome

The task is done, gone from its tier and counted in Done today, and Undo is offered.

## Edge cases

- If marking it done fails, the checkbox unticks again.
- Open cards on All tasks have the same checkbox.
