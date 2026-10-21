---
kind: alternate
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
- text: No Task of today's Plan is unfinished
  kind: condition
  entities:
  - {entity: task, as: done, effect: reads, facts: []}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::wrap-up
- text: The User leaves a note for tomorrow, or none, and wraps up
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::wrap-up
- text: The Product wraps the Day, and the light model writes its summary and reflection
  kind: product
  actor: user
  entities:
  - {entity: day, effect: changes, from: Started, to: Wrapped, facts: [Note for tomorrow, Summary, Reflection]}
  contexts:
    web:
      place: web::wrap-up
---

# Wrap up with nothing left over

## Trigger

Every planned task got done, or was moved out of today.

## Outcome

The day is wrapped with no triage step.
