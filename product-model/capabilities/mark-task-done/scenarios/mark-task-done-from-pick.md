---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User chooses Done on the What now pick
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
- text: The Product marks the picked Task done and closes the pick
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, from: Open, to: Done, facts: []}
  contexts:
    web:
      place: web::today
---

# Finish the task What now picked

## Trigger

The person did the task What now picked.

## Outcome

The task is done and the pick card closes.
