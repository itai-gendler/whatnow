---
kind: primary
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
- text: The User dumps what's on their plate, messy as it comes
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The User picks a pace and, if they like, says how they're feeling
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product saves the brain dump as one captured Task, and tidy-up turns it into tasks right away
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

# Start a day from a brain dump

## Trigger

It is morning, the last day was wrapped up, and the person is ready to start.

## Outcome

Today is started with its first plan; Let's go opens Today.

## Edge cases

- The terminal starts on steady.
- A day started in another tab or the terminal sends this ritual to Today.
- When an integration is on, its pull sits under the dump; in the terminal it is a step of its own.
