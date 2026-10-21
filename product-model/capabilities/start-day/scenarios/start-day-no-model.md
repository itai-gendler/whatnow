---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User begins Good morning
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::today
- text: The User dumps and picks a pace
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: No provider is set up, or the main model fails
  kind: condition
  entities:
  - {entity: settings, effect: reads, facts: [Provider]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product saves the dump as one captured Task as it is
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product starts the Day at that pace and mood
  kind: product
  actor: user
  entities:
  - {entity: day, effect: creates, to: Started, facts: [Date, Pace, Mood, Started]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: 'The Product saves a rough first Plan: due today or overdue is a must, due later a should, undated a could'
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: day, effect: reads, facts: [Pace]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Start a day without the model

## Trigger

The person starts a day while no provider is set up, or the model fails.

## Outcome

The day starts with a rough plan by due date, tagged as rough, and any reconcile suggestions are tagged "rough suggestions".

## Edge cases

- A dump the model fails to tidy is planned as it is, then tidied in the background like any capture.
