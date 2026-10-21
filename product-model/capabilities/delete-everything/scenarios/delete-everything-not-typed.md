---
kind: validation
routes:
  web: Web UI
steps:
- text: The User leaves the confirmation field without "delete everything"
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product keeps Delete everything disabled
  kind: product
  entities: []
  contexts:
    web:
      place: web::general
---

# Keep Delete everything off until the phrase is typed

## Trigger

The person hasn't typed the phrase, or typed something else.

## Outcome

Delete everything stays disabled, and nothing is deleted.
