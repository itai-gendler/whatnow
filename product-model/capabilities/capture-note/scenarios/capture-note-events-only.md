---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User captures a note that only names things at fixed times
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
  - {entity: task, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up adds an Event for each fixed time, today unless the note says otherwise, keeping the note as captured
  kind: product
  actor: user
  entities:
  - {entity: event, effect: creates, facts: [Title, Starts, Ends, As captured]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up removes the note's Task, since it held nothing but fixed times
  kind: product
  actor: user
  entities:
  - {entity: task, effect: removes, from: Open}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Turn a note of fixed times into events

## Trigger

The person captures "standup 9:30, 1:1 with Priya at 2, 45 min".

## Outcome

Today's strip shows the two events, and no task is left behind for the note.

## Edge cases

- An event given no end is kept without one.
