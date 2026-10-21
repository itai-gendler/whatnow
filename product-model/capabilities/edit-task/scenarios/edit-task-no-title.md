---
kind: validation
routes:
  web: Web UI
steps:
- text: The User clears the title and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::task
- text: The Product says "A title is required." and saves nothing
  kind: product
  entities: []
  contexts:
    web:
      place: web::task
---

# Refuse an edit that blanks the title

## Trigger

The person clears the title and saves.

## Outcome

Nothing is saved; the form says a title is required.
