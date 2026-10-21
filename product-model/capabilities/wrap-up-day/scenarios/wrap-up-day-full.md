---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Wrap up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: The Product shows the win line and each Task done today
  kind: product
  entities:
  - {entity: task, as: done, effect: reads, facts: [Title]}
  - {entity: event, effect: reads, facts: [Ends]}
  contexts:
    web:
      place: web::wrap-up
- text: The main model suggests roll over, push or drop for each unfinished Task of today's Plan, with a reason
  kind: product
  actor: user
  entities:
  - {entity: task, as: left, effect: reads, facts: [Title, Feeling, Times pushed]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::wrap-up
- text: The User keeps or overrides each choice and leaves a note for tomorrow
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::wrap-up
- text: The Product pushes and drops each chosen Task together
  kind: product
  actor: user
  entities:
  - {entity: task, as: left, effect: changes, facts: [Not before, Times pushed]}
  - {entity: task, as: dropped, effect: changes, from: Open, to: Dropped, facts: []}
  contexts:
    web:
      place: web::wrap-up
- text: The Product wraps the Day with the note for tomorrow
  kind: product
  actor: user
  entities:
  - {entity: day, effect: changes, from: Started, to: Wrapped, facts: [Note for tomorrow]}
  contexts:
    web:
      place: web::wrap-up
- text: The light model writes the Day's summary for later mornings, then a reflection from it, to the person, in
    the assistant's voice
  kind: product
  actor: user
  entities:
  - {entity: day, effect: changes, facts: [Summary, Reflection]}
  contexts:
    web:
      place: web::wrap-up
- text: The Product shows Goodnight with the Day's reflection
  kind: product
  entities:
  - {entity: day, effect: reads, facts: [Reflection]}
  contexts:
    web:
      place: web::wrap-up
---

# Wrap up with leftovers and a note

## Trigger

The working day is ending and some planned tasks are still open.

## Outcome

The day is wrapped, the leftovers are settled, and Goodnight shows the reflection; Today shows the day's-done card.

## Edge cases

- Unfinished means in today's latest plan, open, and not pushed past today; tasks in the unplanned tray aren't reviewed.
- Goodnight never shows the summary; it is the planner's.
- The summary and reflection are written even if the person closes the page meanwhile.
