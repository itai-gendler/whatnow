---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses × on a ticket in the pick list
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product adds the ticket to its integration's skipped list as a Skipped item
  kind: product
  actor: user
  entities:
  - {entity: skipped-item, effect: creates, facts: [Key, Title]}
  - {entity: jira-integration, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Skip a ticket for good

## Trigger

A ticket keeps showing up that the person will never take.

## Outcome

The ticket is gone from the list and later pulls leave it out; no Undo is offered.
