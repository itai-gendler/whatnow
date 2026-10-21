---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User types a note into the capture box and sends it
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
- text: 'The light model reads the note with the date and the open tasks, and tidies the Task: its title, notes,
    size, energy, feeling, dates and refs'
  kind: product
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Title, Notes, Size, Energy, Feeling, Due, Not before, Refs]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product announces the tidy-up as one Change, saying what it did and offering Undo on the web
  kind: product
  entities:
  - {entity: change, effect: reads, facts: [Made by, What changed]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Capture a note and have it tidied

## Trigger

Something comes to mind and the person wants it out of their head.

## Outcome

Within seconds the note is a tidy task with its size, energy and feeling, and one undo would take the tidy-up back.

## Edge cases

- A task that tidy-up makes due today sets off a replan; any other new task waits in the unplanned tray.
- A note typed during a ritual goes through the same tidy-up.
