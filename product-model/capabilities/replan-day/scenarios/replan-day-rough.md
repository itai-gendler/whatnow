---
kind: edge
routes:
  web: Web UI
steps:
- text: The User chooses Replan in the unplanned tray
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: No provider is set up, or the main model fails
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider]}
  contexts:
    web:
      place: web::today
- text: 'The Product saves a rough Plan: each eligible Task due today or overdue is a must, due later a should by
    due date, undated a could by age'
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: task, effect: reads, facts: [Due]}
  contexts:
    web:
      place: web::today
---

# Make a rough plan when the model is out

## Trigger

A replan runs while no provider is set up, or the model's plan is rejected twice, fails, or takes over a minute.

## Outcome

Today shows a rough plan by due date, tagged "rough plan, model was out".

## Edge cases

- A reply that names an unknown or ineligible task, a task twice, or a bad tier is sent back once with the problems before code takes over.
