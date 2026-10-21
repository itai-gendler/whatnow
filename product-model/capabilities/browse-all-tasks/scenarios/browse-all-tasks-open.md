---
kind: primary
routes:
  web: Web UI
steps:
- text: The User opens All tasks
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::all-tasks
- text: The Product lists every open Task by due date, undated last, then newest first, with its due and not-before
    dates
  kind: product
  entities:
  - {entity: task, effect: reads, facts: [Title, Size, Energy, Feeling, Due, Not before]}
  contexts:
    web:
      place: web::all-tasks
---

# Browse open tasks

## Trigger

The person wants to see everything still to do, not just today.

## Outcome

All tasks lists every open task by due date, undated last.
