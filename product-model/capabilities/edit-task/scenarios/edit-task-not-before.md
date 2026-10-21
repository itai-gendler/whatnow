---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User opens a Task from All tasks
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::all-tasks
- text: The User sets the not-before date and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product saves the Task's new not-before date as an ordinary edit, without counting a push
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Not before]}
  contexts:
    web:
      place: web::task
---

# Set a not-before date by hand

## Trigger

The person edits a task's not-before date in the form instead of pushing it.

## Outcome

The task is put off until that date, and its push count is unchanged.
