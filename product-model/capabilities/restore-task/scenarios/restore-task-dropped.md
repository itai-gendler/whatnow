---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Restore on a dropped Task under Dropped
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::all-tasks
- text: The Product sets the Task back to open
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, from: Dropped, to: Open, facts: []}
  contexts:
    web:
      place: web::all-tasks
---

# Restore a dropped task

## Trigger

The person dropped a task and wants it back.

## Outcome

The task is open again and waits in the unplanned tray, and Undo is offered.
