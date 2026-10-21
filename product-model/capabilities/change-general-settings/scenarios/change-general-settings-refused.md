---
kind: validation
routes:
  web: Web UI
steps:
- text: The User saves the General page with a value outside its limits
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product refuses the whole save and says which value is wrong
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Event alerts, Allowed hosts]}
  contexts:
    web:
      place: web::general
---

# Refuse settings outside their limits

## Trigger

The person saves an event alert time outside 1 to 60 minutes, an allowed host with a scheme or port, or an incomplete model setup.

## Outcome

Nothing is saved; an error says what is wrong.
