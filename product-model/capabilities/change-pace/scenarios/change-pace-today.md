---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User picks another pace level for the Day
  kind: actor
  actor: user
  entities:
  - {entity: day, effect: reads, facts: [Pace]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product sets the Day's pace
  kind: product
  actor: user
  entities:
  - {entity: day, effect: changes, facts: [Pace]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product replans the Day for the new pace, and the new Plan arrives on its own
  kind: product
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: day, effect: reads, facts: [Pace, Mood]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Change the pace

## Trigger

After a draining 1:1, the person drops the pace to gentle.

## Outcome

The day's pace is gentle, Undo is offered, and a fresh plan follows.

## Edge cases

- The terminal moves one level at a time and says so when the pace is already at the end.
