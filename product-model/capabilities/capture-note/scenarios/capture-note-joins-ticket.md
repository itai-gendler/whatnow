---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User captures a note naming a ticket key
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product saves the note at once as an open Task titled with its first line, keeping the words as captured
  kind: product
  actor: user
  entities:
  - {entity: task, as: note, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: An open Task already carries the same ticket key in its refs
  kind: condition
  entities:
  - {entity: task, as: existing, effect: reads, facts: [Refs]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up adds the note's feeling to that Task instead of making another
  kind: product
  actor: user
  entities:
  - {entity: task, as: existing, effect: changes, facts: [Feeling]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up removes the note's own Task, which has joined the other
  kind: product
  actor: user
  entities:
  - {entity: task, as: note, effect: removes, from: Open}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Join a note to the open task with its ticket key

## Trigger

The person captures a note about a ticket that an open task already carries, such as "FLEX1-666 is stressing me out".

## Outcome

No second task is made: the feeling lands on the existing task and the note is gone.

## Edge cases

- Only ticket keys such as FLEX1-666 join; a looser match never does.
- A done task's key doesn't count: a note about it means the work came back.
