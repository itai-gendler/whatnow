---
kind: validation
routes:
  web: Web UI
steps:
- text: The User saves the form with a blank title
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product says "A title is required." and adds nothing
  kind: product
  entities: []
  contexts:
    web:
      place: web::task
---

# Refuse a task with no title

## Trigger

The person saves the form with a blank title.

## Outcome

Nothing is added; the form says a title is required.
