---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User adds tickets already on the list as Task refs
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product leaves out each ticket already a ref on a Task or skipped, and adds nothing for them
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Refs]}
  - {entity: skipped-item, effect: reads, facts: [Key]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Add a ticket only once

## Trigger

The person adds again tickets already added, such as with a double click or from another tab.

## Outcome

Each ticket is on the list once.
