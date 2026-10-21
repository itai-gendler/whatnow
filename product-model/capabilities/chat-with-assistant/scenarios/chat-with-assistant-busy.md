---
kind: validation
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: A reply is still being written
  kind: condition
  entities:
  - {entity: chat-message, effect: reads, facts: []}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The User sends another message
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product refuses it until the reply is done
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
---

# Wait for the reply being written

## Trigger

The person sends a second message, from another tab, while a reply is still being written.

## Outcome

The second message is not sent; the dock says "One sec, still answering." and keeps the text in the input.
