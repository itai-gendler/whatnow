---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User chooses Undo on a chat reply
  kind: actor
  actor: user
  entities:
  - {entity: change, effect: reads, facts: [What changed]}
  - {entity: chat-message, effect: reads, facts: [Changes made]}
  contexts:
    web:
      place: web::chat
- text: The Product removes each Task the reply added, newest first
  kind: product
  actor: user
  entities:
  - {entity: task, effect: removes, from: Open}
  contexts:
    web:
      place: web::chat
- text: The Product marks the Change undone, and the reply shows it
  kind: product
  actor: user
  entities:
  - {entity: change, effect: changes, from: Applied, to: Undone, facts: []}
  contexts:
    web:
      place: web::chat
---

# Undo everything a chat reply did

## Trigger

The assistant added steps the person doesn't want.

## Outcome

Every task the reply added is gone, and the reply's button reads "undone".
