---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Undo after a push
  kind: actor
  actor: user
  entities:
  - {entity: change, effect: reads, facts: [What changed]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product puts the Task back as it was before, its not-before date and push count included
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Not before, Times pushed]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product marks the Change undone
  kind: product
  actor: user
  entities:
  - {entity: change, effect: changes, from: Applied, to: Undone, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Undo a push right after it

## Trigger

The person pushed a task by mistake and Undo is still offered.

## Outcome

The task is back as it was before the push, and every open screen shows it.

## Edge cases

- On the web, Undo is offered for about eight seconds, longer while the pointer rests on it.
- In the terminal, u with nothing of the person's own to undo says "Nothing to undo".
