---
kind: alternate
routes:
  web: Web UI
steps:
- text: A nudge is due and notifications aren't allowed in this browser
  kind: condition
  unattended: true
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web
- text: The Product shows the nudge as a note in the open page
  kind: product
  entities: []
  contexts:
    web:
      place: web
---

# Nudge in the page without notifications

## Trigger

A nudge is due while the browser doesn't allow notifications.

## Outcome

A yellow note shows in the page, lasts longer than an offered Undo, and stays while the pointer rests on it.

## Edge cases

- With two tabs open, a notification is shown once.
- A nudge that comes while the tab is hidden waits there until the person looks.
