---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses Move › and a tier on a Task card
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::today
- text: The Product saves a new Plan version with the Task in that tier and "You moved this here." as its rationale,
    keeping the opening
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
---

# Move a task to another tier

## Trigger

The person disagrees with where the plan put a task.

## Outcome

Today shows the task in the chosen tier at once, and the plan's other entries are as they were.

## Edge cases

- The card's own tier is greyed out.
