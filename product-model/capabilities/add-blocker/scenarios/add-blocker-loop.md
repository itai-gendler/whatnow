---
kind: validation
routes:
  web: Web UI
steps:
- text: The User picks a task that already waits on this Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::task
- text: The Product refuses to add the Blocker, since both tasks would stay blocked for good
  kind: product
  actor: user
  entities:
  - {entity: blocker, effect: reads, facts: [Blocking task]}
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::task
---

# Refuse a blocker that would close a loop

## Trigger

The person tries to make a task wait on a task that already waits on it, directly or through others.

## Outcome

No blocker is added; the sheet shows why.
