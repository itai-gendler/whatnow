---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User says "undo that"
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
- text: The assistant takes back the most recent Change made by the assistant or tidy-up, leaving out the current
    reply's own
  kind: product
  actor: user
  entities:
  - {entity: change, effect: changes, from: Applied, to: Undone, facts: []}
  - {entity: task, effect: changes, facts: [Title, Notes, Size, Energy, Feeling, Due, Not before]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves the reply saying what was undone
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

# Undo the last thing by asking

## Trigger

The person says "undo that" after the assistant or tidy-up did something they didn't want.

## Outcome

The most recent change made by the assistant or tidy-up is taken back whole.
