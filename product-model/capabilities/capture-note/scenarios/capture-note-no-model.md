---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User captures a note
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
- text: No provider is set up, or the light model fails
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider, API key]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product leaves the Task as captured, fully usable
  kind: product
  entities:
  - {entity: task, effect: reads, facts: [Title, As captured]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Capture without a working model

## Trigger

The person captures a note while no provider is set up, or while the model fails.

## Outcome

The note stays an ordinary open task, titled with its first line, and waits in the unplanned tray.

## Edge cases

- A note typed while the model is out is not tidied later on its own; it stays as captured.
