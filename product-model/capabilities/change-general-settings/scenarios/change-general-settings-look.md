---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User picks a look under Look
  kind: actor
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Look]}
  contexts:
    web:
      place: web::general
- text: The Product saves the look at once, on top of the last saved Settings rather than the form's unsaved edits
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Look]}
  contexts:
    web:
      place: web::general
---

# Pick a look

## Trigger

The person wants whatnow to look like a terminal.

## Outcome

The whole web UI takes the Terminal look at once.
