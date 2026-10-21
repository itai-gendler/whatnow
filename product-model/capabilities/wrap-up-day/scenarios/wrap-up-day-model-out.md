---
kind: edge
routes:
  web: Web UI
steps:
- text: The User chooses Wrap up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: No provider is set up, or the light model fails
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider]}
  contexts:
    web:
      place: web::wrap-up
- text: The User wraps up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::wrap-up
- text: The Product wraps the Day with an empty summary and no reflection
  kind: product
  actor: user
  entities:
  - {entity: day, effect: changes, from: Started, to: Wrapped, facts: [Note for tomorrow]}
  contexts:
    web:
      place: web::wrap-up
---

# Wrap up while the model is out

## Trigger

The person wraps up while no provider is set up, or the model fails.

## Outcome

The day still wraps and Goodnight has no reflection; without a provider, suggestions are tagged "rough suggestions" and all start on roll over.
