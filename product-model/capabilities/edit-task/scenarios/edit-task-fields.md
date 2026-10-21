---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Edit on a Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
- text: The User edits the title, notes, size, energy, feeling or dates, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product saves every field of the Task, leaving its words as captured as they were
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Title, Notes, Size, Energy, Feeling, Due, Not before]}
  contexts:
    web:
      place: web::task
---

# Edit a task's details

## Trigger

A task's details are wrong or missing, such as its size or due date.

## Outcome

The task carries the new details everywhere, and Undo is offered.

## Edge cases

- Escape or ✕ closes the sheet without saving.
- Giving a task today's due date sets off a replan.
