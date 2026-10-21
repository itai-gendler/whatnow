---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Test connection
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product sends a tiny request to the main model, then the light model, with the saved key
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Provider, API key, Main model, Light model, Base URL]}
  contexts:
    web:
      place: web::general
- text: Both answer, and the Product says Connected
  kind: product
  entities: []
  contexts:
    web:
      place: web::general
---

# Test a working connection

## Trigger

The person has saved a provider and key and wants to know they work.

## Outcome

"Connected" shows beside the button.
