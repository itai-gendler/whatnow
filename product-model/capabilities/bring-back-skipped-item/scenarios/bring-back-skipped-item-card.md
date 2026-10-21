---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses bring back beside a Skipped item on its integration's card
  kind: actor
  actor: user
  entities:
  - {entity: skipped-item, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::integrations
- text: The Product removes the Skipped item
  kind: product
  actor: user
  entities:
  - {entity: skipped-item, effect: removes}
  - {entity: google-calendar-integration, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
---

# Bring back a skipped meeting series

## Trigger

The person skipped a series by mistake.

## Outcome

The series is off the skipped list, and the next pull brings today's occurrence in again.
