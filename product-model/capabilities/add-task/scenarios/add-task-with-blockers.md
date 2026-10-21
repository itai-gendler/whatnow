---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User fills in a new form and picks the open work it has to wait on
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The User saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product adds the open Task
  kind: product
  actor: user
  entities:
  - {entity: task, as: new, effect: creates, to: Open, facts: [Title, Added by]}
  contexts:
    web:
      place: web::task
- text: The Product adds a Blocker on it for each picked task
  kind: product
  actor: user
  entities:
  - {entity: blocker, effect: creates, facts: [Blocking task]}
  - {entity: task, as: new, effect: reads, facts: []}
  - {entity: task, as: first, effect: reads, facts: []}
  contexts:
    web:
      place: web::task
---

# Add a task that waits on others

## Trigger

The person adds a task that can't start until other open tasks are finished.

## Outcome

The new task exists with its blockers, and shows "⛓ waits on N".
