---
kind: primary
routes:
  web: Web UI
steps:
- text: The User asks for a blank form from Today
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: The User fills in the title and any notes, size, energy, feeling, due date and not-before date, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product adds an open Task with exactly those fields, added by the User
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, Notes, Size, Energy, Feeling, Due, Not before, Added
        by]}
  contexts:
    web:
      place: web::task
---

# Add a task through the form

## Trigger

The person knows exactly what the task is and wants it added as typed.

## Outcome

The new task waits in the unplanned tray, and Undo is offered.

## Edge cases

- + Task is also in the All tasks header.
