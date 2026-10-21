---
kind: primary
routes:
  web: Web UI
steps:
- text: The User opens the Jira card and fills in the address, a personal access token and a search
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
- text: The User chooses Save on the card
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
- text: The Product saves the address and search, and keeps the token in the system keychain, showing it only as
    saved
  kind: product
  actor: user
  entities:
  - {entity: jira-integration, effect: changes, facts: [Address, Personal access token, Search (JQL)]}
  contexts:
    web:
      place: web::integrations
---

# Set up Jira

## Trigger

The person wants their Jira tickets offered in the morning.

## Outcome

Jira is ready to pull once it is on.

## Edge cases

- Nothing is prefilled in the search.
