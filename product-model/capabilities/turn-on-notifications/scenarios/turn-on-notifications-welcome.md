---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User chooses Turn on notifications on the Nudges step
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The browser asks, and the User answers
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
---

# Turn on notifications in first-run setup

## Trigger

The person reaches the Nudges step of Welcome.

## Outcome

Notifications are allowed, or the person moved on without them and nudges will show in the page.

## Edge cases

- The three nudge kinds stay on either way.
