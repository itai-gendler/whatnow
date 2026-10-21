---
kind: automatic
routes:
  web: Web UI
steps:
- text: Today's Day is wrapped with a summary and no reflection
  kind: condition
  unattended: true
  entities:
  - {entity: day, effect: reads, facts: [Summary, Reflection]}
  contexts:
    web:
      place: web::today
- text: The light model writes the reflection from the summary in the background, and the Product saves it
  kind: product
  entities:
  - {entity: day, effect: changes, facts: [Reflection]}
  contexts:
    web:
      place: web::today
---

# Write a missing reflection later

## Trigger

A wrapped day has a summary but no reflection, because the reflection failed at wrap-up.

## Outcome

The reflection appears on the day's-done card at the next refresh.

## Edge cases

- A reflection that fails here isn't tried again until whatnow restarts.
