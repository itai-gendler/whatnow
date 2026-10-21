---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User writes an assistant style and About me, within 500 and 1000 characters, and goes on
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The Product saves both to the Settings
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Assistant style, About me]}
  contexts:
    web:
      place: web::welcome
---

# Tell the planner about yourself in first-run setup

## Trigger

In Welcome, the person writes how they like to be spoken to and how they work.

## Outcome

Every plan, pick and chat from then on reads both.

## Edge cases

- Skip goes on without saving.
