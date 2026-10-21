---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses ✕ beside a Blocker under "Blocked by"
  kind: actor
  actor: user
  entities:
  - {entity: blocker, effect: reads, facts: [Blocking task]}
  contexts:
    web:
      place: web::task
- text: The Product removes the Blocker
  kind: product
  actor: user
  entities:
  - {entity: blocker, effect: removes}
  contexts:
    web:
      place: web::task
---

# Free a task from a blocker

## Trigger

A task no longer has to wait on another.

## Outcome

The task is free to start, unless other blockers remain, and Undo is offered.

## Edge cases

- A finished or dropped blocking task already stops blocking without being removed.
