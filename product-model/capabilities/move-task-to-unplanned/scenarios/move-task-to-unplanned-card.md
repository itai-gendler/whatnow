---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Move › Unplanned on a planned Task
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::today
- text: The Product saves a new Plan version without the Task, keeping the opening
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
---

# Take a task out of the plan

## Trigger

The person wants a planned task off today's plan without letting it go.

## Outcome

The task waits in the unplanned tray and stays open.

## Edge cases

- Once the day is wrapped, Move › isn't offered.
