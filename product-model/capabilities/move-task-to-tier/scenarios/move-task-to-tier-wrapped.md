---
kind: validation
routes:
  web: Web UI
steps:
- text: The Day is wrapped
  kind: condition
  entities:
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
- text: The User looks for Move › on a Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
- text: The Product offers no Move ›, and refuses a move of a wrapped day's Plan
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: reads, facts: []}
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
---

# No moving once the day is wrapped

## Trigger

The person looks for Move › after wrapping up.

## Outcome

Move › is not offered; the wrapped day's plan stays as it was.
