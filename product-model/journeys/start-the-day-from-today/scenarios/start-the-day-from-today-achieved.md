---
kind: primary
result: achieved
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User opens Today
  kind: actor
  actor: user
  capability: view-today
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product finds nothing started for today's date and takes the User to Good morning
  kind: product
  actor: user
  capability: view-today
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::today
- text: The User begins, dumps what's on their plate and picks a pace
  kind: actor
  actor: user
  capability: start-day
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product starts the Day
  kind: product
  actor: user
  capability: start-day
  entities:
  - {entity: day, effect: creates, to: Started, facts: [Date, Pace, Mood, Started]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product saves the Day's first Plan and reveals it
  kind: product
  actor: user
  capability: start-day
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: day, effect: reads, facts: [Pace]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Open Today and be taken through the morning

## Trigger

The person opens Today on a date with no started day.

## Outcome

Today is started and planned, and Let's go, or enter in the terminal, opens it.
