---
kind: edge
routes:
  web: Web UI
steps:
- text: The User opens the Nudges section of the General page
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The browser blocks notifications
  kind: condition
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product says nudges will show in the page instead
  kind: product
  entities: []
  contexts:
    web:
      place: web::general
---

# Notifications blocked in the browser

## Trigger

The browser has notifications blocked for whatnow.

## Outcome

The row says "Blocked in your browser. Nudges show in the page instead."
