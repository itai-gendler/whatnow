---
kind: automatic
routes:
  web: Web UI
steps:
- text: An Event with a set end has just ended, and the event-end nudge is on
  kind: condition
  unattended: true
  entities:
  - {entity: event, effect: reads, facts: [Title, Ends]}
  - {entity: settings, effect: reads, facts: [When an event ends]}
  contexts:
    web:
      place: web
- text: The Product shows the nudge with a What now? to click
  kind: product
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web
---

# Nudge when an event ends

## Trigger

An event with a set end has just ended.

## Outcome

The person sees "Standup's done. What now?"; clicking it opens a fresh What now pick.

## Edge cases

- An event with no end gets no event-end nudge.
