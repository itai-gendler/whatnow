---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User asks the assistant to move the dentist to Thursday
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves the message under today's date
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: asked, effect: creates, facts: [Date, From, Text]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The assistant finds the dentist Event among the coming week's and moves its start and end to Thursday
  kind: product
  actor: user
  entities:
  - {entity: event, effect: changes, facts: [Starts, Ends]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves the reply with each action it took and an Undo, and streams it into every open chat
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: reply, effect: creates, facts: [Date, From, Text, Changes made]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
---

# Move an event by asking

## Trigger

The person asks "push the dentist to Thursday".

## Outcome

The dentist appointment is on Thursday, and the reply carries an Undo.

## Edge cases

- Putting a task off goes through a push, never an edit of its not-before date, so pushes stay counted.
