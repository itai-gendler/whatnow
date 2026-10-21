---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User sends a message
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
- text: No provider is set up
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider, API key]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves a failed reply saying to add a provider in settings
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: reply, effect: creates, facts: [Date, From, Text, Error]}
  - {entity: settings, effect: reads, facts: []}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
---

# Chat with no provider set up

## Trigger

The person sends a message before a provider is set up.

## Outcome

The reply says no AI provider is set up yet, with a link to Settings on the web.
