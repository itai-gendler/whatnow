---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses Undo on an older Change
  kind: actor
  actor: user
  entities:
  - {entity: change, as: older, effect: reads, facts: [What changed]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: A later Change, not undone, touched the same Task
  kind: condition
  entities:
  - {entity: change, as: later, effect: reads, facts: [What changed]}
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product refuses and leaves everything as it is
  kind: product
  actor: user
  entities:
  - {entity: change, as: older, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Refuse an undo that would overwrite a later edit

## Trigger

The person undoes an older change after something newer touched the same task, such as finishing it in another tab.

## Outcome

Nothing is undone; an error says what was edited since, and the later edit stands.

## Edge cases

- Restoring a removed Blocker that would now close a loop is refused the same way.
- Undoing a pull is refused once the same meeting has been pulled again since.
