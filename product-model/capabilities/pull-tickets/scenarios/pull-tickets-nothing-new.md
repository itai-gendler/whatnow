---
kind: alternate
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
- text: Each ticket found is already a ref on a Task or skipped
  kind: condition
  entities:
  - {entity: task, effect: reads, facts: [Refs]}
  - {entity: skipped-item, effect: reads, facts: [Key]}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: The Product says there is nothing new
  kind: product
  entities: []
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
---

# Pull with nothing new to offer

## Trigger

Every ticket the search finds is already on the list or skipped.

## Outcome

The results say "Nothing new in Jira".
