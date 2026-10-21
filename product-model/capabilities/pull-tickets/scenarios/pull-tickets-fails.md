---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User pulls Jira
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: Jira can't be reached or refuses the request
  kind: condition
  entities:
  - {entity: jira-integration, effect: reads, facts: [Address]}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: The Product shows the error, never the token, with Retry
  kind: product
  entities: []
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
---

# Pull when the source can't answer

## Trigger

Jira can't be reached, rejects the token or the search, or Review Queue isn't running.

## Outcome

The results show a plain error with Retry; nothing is offered.

## Edge cases

- Errors read like "Can't reach Jira — on the VPN?", "Jira rejected the token", Jira's own words for a bad search, or "Can't reach Review Queue — is it running?".
