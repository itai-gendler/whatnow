---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User chooses × on a pulled recurring Event, then Just today
  kind: actor
  actor: user
  entities:
  - {entity: event, effect: reads, facts: [Title, Starts]}
  contexts:
    web:
      place: web::good-morning
- text: The Product removes that Event, remembering it was removed so later pulls leave it out
  kind: product
  actor: user
  entities:
  - {entity: event, effect: removes}
  contexts:
    web:
      place: web::good-morning
---

# Remove just today's meeting from a pull

## Trigger

Today's occurrence of a recurring meeting is one the person won't attend.

## Outcome

Today's occurrence is gone and later pulls leave it out; the series still comes on other days.
