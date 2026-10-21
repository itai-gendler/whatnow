---
kind: edge
routes:
  web: Web UI
steps:
- text: The User chooses Wrap up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: The User settles the list and wraps up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::wrap-up
- text: A Task on the list was finished elsewhere since it loaded
  kind: condition
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::wrap-up
- text: The Product refuses the whole wrap-up before writing anything, and shows the fresh list
  kind: product
  actor: user
  entities:
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::wrap-up
---

# Wrap up after a triaged task changed elsewhere

## Trigger

A task on the wrap-up list is finished in another tab before the person wraps up.

## Outcome

Nothing is written; the fresh list shows with "Something changed, here's the fresh list." and the other choices are kept.

## Edge cases

- A day wrapped meanwhile in another tab sends this ritual to Today.
