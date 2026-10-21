---
kind: edge
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
- text: The provider refuses one of the models
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Main model, Light model]}
  contexts:
    web:
      place: web::general
- text: The Product shows the error, prefixed with that model
  kind: product
  entities: []
  contexts:
    web:
      place: web::general
---

# Test a connection that fails

## Trigger

The key is wrong, or one of the models doesn't exist on the server.

## Outcome

The error shows beside the button, naming the model that failed.
