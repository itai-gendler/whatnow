---
kind: alternate
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
- text: The User chooses Skip on the brain dump, then picks a pace
  kind: actor
  actor: user
  entities: []
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
- text: The main model plans the Day from every eligible Task, the free time until the end of day, About me and
    the last day's summary and note, and the Product saves it as the first Plan
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: task, effect: reads, facts: [Title, Size, Energy, Feeling, Due, Times pushed]}
  - {entity: day, effect: reads, facts: [Pace, Mood]}
  - {entity: settings, effect: reads, facts: [About me, End of day]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product reveals the Plan's opening and each tier's titles
  kind: product
  entities:
  - {entity: plan, effect: reads, facts: [Opening, Tiers]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Start without a brain dump

## Trigger

The person has nothing new to add this morning.

## Outcome

Today is started with a plan made from the tasks already there.
