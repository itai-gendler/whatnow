---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User begins Good morning
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::today
- text: The User settles the list, dumps and asks to get going
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: A Task on the list was finished elsewhere since the list loaded
  kind: condition
  entities:
  - {entity: task, as: left, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product saves the brain dump as one captured Task, and tidy-up turns it into tasks right away
  kind: product
  actor: user
  entities:
  - {entity: task, as: dump, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product refuses to start, applying no triage, and shows the fresh list with the choices kept; the dump
    box is cleared, since the dump is saved
  kind: product
  actor: user
  entities:
  - {entity: task, as: left, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Start after a triaged task changed elsewhere

## Trigger

While the person reconciles, a task on the list is finished in another tab.

## Outcome

Nothing is triaged and the day doesn't start yet; the fresh list shows with "Something changed, here's the fresh list." and the choices for tasks still on it are kept.
