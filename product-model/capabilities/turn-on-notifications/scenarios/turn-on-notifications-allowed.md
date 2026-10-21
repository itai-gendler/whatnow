---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Turn on notifications
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The browser asks, and the User allows it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product shows "Notifications on"
  kind: product
  entities: []
  contexts:
    web:
      place: web::general
---

# Allow notifications

## Trigger

The person wants nudges even when the whatnow tab is in the background.

## Outcome

"Notifications on" shows, and nudges arrive as system notifications.
