---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Not this one on the pick
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The User says why, such as "can't face it"
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product adds the reason to the end of the Task's feeling
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Feeling]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The main model picks again from every eligible Task except that one
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title, Feeling]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Pass with a reason

## Trigger

What now picked the report the person is dreading, and they say "can't face it".

## Outcome

The reason is on the task's feeling, and a new pick, never the same task, takes its place.
