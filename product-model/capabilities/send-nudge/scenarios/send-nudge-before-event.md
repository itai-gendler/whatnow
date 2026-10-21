---
kind: automatic
routes:
  web: Web UI
steps:
- text: An Event starts within the alert lead time, and the before-event nudge is on
  kind: condition
  unattended: true
  entities:
  - {entity: event, effect: reads, facts: [Title, Starts]}
  - {entity: settings, effect: reads, facts: [Event alerts, Before each event]}
  contexts:
    web:
      place: web
- text: The Product shows the nudge naming the Event and the minutes left
  kind: product
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web
---

# Nudge before an event

## Trigger

An event is about to start: it is the alert lead time before it.

## Outcome

The person sees "Standup in 10 min, find a stopping point."

## Edge cases

- An event added inside its own lead time gets no before-event nudge; it is news already.
