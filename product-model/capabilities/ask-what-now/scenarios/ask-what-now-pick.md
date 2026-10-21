---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User asks What now?
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The main model weighs every eligible Task, the free time before the next Event, the pace and the mood, and
    picks one unblocked Task with a reason
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title, Size, Energy, Feeling, Due, Times pushed]}
  - {entity: event, effect: reads, facts: [Starts, Ends]}
  - {entity: day, effect: reads, facts: [Pace, Mood]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product shows the picked Task and the reason
  kind: product
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Get one pick with a reason

## Trigger

The person is stuck and asks what to do now.

## Outcome

A card shows one task to do now and why; in the terminal the list points at it with the reason.

## Edge cases

- A pick that names an unknown, ineligible or blocked task is sent back once with the problem; if it fails again, code picks.
- ✕ closes the card.
