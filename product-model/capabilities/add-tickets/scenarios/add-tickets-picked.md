---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User ticks two tickets and chooses Add 2
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product adds an open Task for each ticket, titled as in the pick list, with its description as notes
    and its key and link as its ref
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, Notes, Refs, Added by]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product replaces the pick list with "Added 2"
  kind: product
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Add the tickets ticked

## Trigger

The person ticks two tickets from the pull.

## Outcome

Two tasks wait in the unplanned tray, the list says "Added 2", and one undo removes both.
