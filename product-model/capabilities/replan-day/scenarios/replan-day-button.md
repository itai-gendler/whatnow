---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Replan in the unplanned tray
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
- text: The main model plans the Day again from every eligible Task, keeping what still fits and weighing moves
    made by hand
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title, Size, Energy, Feeling, Due, Not before, Times pushed]}
  - {entity: day, effect: reads, facts: [Pace, Mood]}
  - {entity: event, effect: reads, facts: [Starts, Ends]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::today
- text: The Product saves the new Plan version and shows it
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  contexts:
    web:
      place: web::today
---

# Replan from the tray

## Trigger

New tasks are waiting in the unplanned tray and the person wants them considered.

## Outcome

A new plan version replaces the tiers, with an opening saying briefly what changed.

## Edge cases

- Replan shows only while the tray has tasks and the day isn't wrapped.
- A plan has no undo; the next replan just makes another version.
