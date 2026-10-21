---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User fills in Review Queue's address and, optionally, a minimum score, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
- text: The Product saves both
  kind: product
  actor: user
  entities:
  - {entity: review-queue-integration, effect: changes, facts: [Address, Minimum score]}
  contexts:
    web:
      place: web::integrations
---

# Set up Review Queue

## Trigger

The person runs Review Queue and wants its queue offered.

## Outcome

Review Queue is ready to pull once it is on.

## Edge cases

- A minimum score that isn't a whole number makes the pull fail with "minimum score must be a whole number".
