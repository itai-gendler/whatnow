---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User edits the search, leaves the token blank, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
- text: The Product saves the new search and keeps the token already in the keychain
  kind: product
  actor: user
  entities:
  - {entity: jira-integration, effect: changes, facts: [Search (JQL)]}
  contexts:
    web:
      place: web::integrations
---

# Edit the search and keep the saved token

## Trigger

The person edits the Jira search and leaves the token field blank.

## Outcome

The new search is saved and the saved token stays.
