---
kind: primary
routes:
  web: Web UI
steps:
- text: The User opens a Task in the sheet and picks another open one it has to wait on
  kind: actor
  actor: user
  entities:
  - {entity: task, as: waiting, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::task
- text: 'The Product adds a Blocker: the Task now waits on the one picked'
  kind: product
  actor: user
  entities:
  - {entity: blocker, effect: creates, facts: [Blocking task]}
  - {entity: task, as: waiting, effect: reads, facts: []}
  - {entity: task, as: blocking, effect: reads, facts: []}
  contexts:
    web:
      place: web::task
---

# Make a task wait on another

## Trigger

The person realises one task has to happen before another.

## Outcome

The task shows "⛓ waits on 1", the other shows "unblocks 1", and Undo is offered.

## Edge cases

- Only open tasks other than the task itself, and not already blocking it, are offered.
- A Blocker that involves a must sets off a replan.
