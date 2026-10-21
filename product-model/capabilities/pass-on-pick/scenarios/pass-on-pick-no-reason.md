---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Not this one and leaves the reason empty
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The main model picks again from every eligible Task except that one
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Pass without a reason

## Trigger

The person passes on the pick without saying why.

## Outcome

A new pick appears; the passed task's feeling is unchanged.

## Edge cases

- If nothing else is free to start, the note says there is nothing to do right now.
