---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User asks the assistant for several things
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
- text: The assistant adds an open Task, and then the provider fails
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, Added by]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves a failed reply with the actions so far, their Undo, and a plain explanation
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: reply, effect: creates, facts: [Date, From, Text, Changes made, Error]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
---

# Keep what was done when the provider fails

## Trigger

The provider fails partway through a reply, for a bad key, a rate limit or an outage.

## Outcome

The reply shows as failed with "Check settings"; anything it already did stays done and keeps its Undo. Sending again retries.

## Edge cases

- A reply the model declines, or one cut off for length, says so in plain words.
- After ten rounds of actions, the reply stops and says to ask to keep going.
