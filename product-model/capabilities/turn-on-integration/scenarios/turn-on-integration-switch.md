---
kind: primary
routes:
  web: Web UI
steps:
- text: The User turns on the switch on the Jira card
  kind: actor
  actor: user
  entities:
  - {entity: jira-integration, effect: reads, facts: ['On']}
  contexts:
    web:
      place: web::integrations
- text: The Product saves the Jira integration as on and opens its card
  kind: product
  actor: user
  entities:
  - {entity: jira-integration, effect: changes, facts: ['On']}
  contexts:
    web:
      place: web::integrations
---

# Turn Jira on

## Trigger

Jira is set up and the person wants it in the morning.

## Outcome

Jira is on: the morning offers its pull, and the card's Pull works.
