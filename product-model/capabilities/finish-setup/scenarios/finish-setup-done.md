---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Next on the Nudges step
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The Product saves the Settings as set up
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Setup finished]}
  contexts:
    web:
      place: web::welcome
- text: The Product shows "You're set" with a button to start the first morning
  kind: product
  entities: []
  contexts:
    web:
      place: web::welcome
---

# Finish every setup step

## Trigger

The person has gone through every step of Welcome.

## Outcome

Setup is finished, and the last step offers Start my day.
