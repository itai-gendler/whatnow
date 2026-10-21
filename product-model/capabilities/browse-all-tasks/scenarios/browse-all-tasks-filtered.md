---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User picks Future, Blocked, Done, Dropped or All
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::all-tasks
- text: 'The Product lists only matching Task entries: open with a later not-before date, open and waiting on an
    open Blocker, done, dropped, or all of them'
  kind: product
  entities:
  - {entity: task, effect: reads, facts: [Title, Not before]}
  - {entity: blocker, effect: reads, facts: []}
  contexts:
    web:
      place: web::all-tasks
---

# Filter all tasks

## Trigger

The person looks for tasks put off, blocked, done or dropped.

## Outcome

Only the tasks that filter names are listed.
