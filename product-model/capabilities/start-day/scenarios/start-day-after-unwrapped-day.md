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
- text: The last Day before today was never wrapped up
  kind: condition
  entities:
  - {entity: day, as: last, effect: reads, facts: [Date]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The main model suggests roll over, push or drop for each unfinished Task of that Day's plan, with a one-line
    reason
  kind: product
  actor: user
  entities:
  - {entity: task, as: left, effect: reads, facts: [Title, Feeling, Times pushed]}
  - {entity: day, as: last, effect: reads, facts: [Pace]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product opens with that Day's win, such as "Last time you got 4 things done", and the triage list with
    each suggestion chosen
  kind: product
  entities:
  - {entity: task, as: left, effect: reads, facts: [Title]}
  - {entity: day, as: last, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The User keeps or overrides each choice, picking a date for a push, then dumps, and picks a pace
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
  - {entity: task, as: dump, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product pushes and drops each chosen Task together, and leaves rolled-over ones open
  kind: product
  actor: user
  entities:
  - {entity: task, as: left, effect: changes, facts: [Not before, Times pushed]}
  - {entity: task, as: dropped, effect: changes, from: Open, to: Dropped, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product wraps the last Day with no note, and the light model writes its summary for the planner
  kind: product
  actor: user
  entities:
  - {entity: day, as: last, effect: changes, from: Started, to: Wrapped, facts: [Summary]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product starts the Day at that pace and mood
  kind: product
  actor: user
  entities:
  - {entity: day, as: today, effect: creates, to: Started, facts: [Date, Pace, Mood, Started]}
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
  - {entity: task, as: left, effect: reads, facts: [Title, Size, Energy, Feeling, Due, Times pushed]}
  - {entity: day, as: today, effect: reads, facts: [Pace, Mood]}
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

# Settle an unwrapped last day, then start

## Trigger

The person didn't wrap up the last day they used whatnow, and opens it the next morning.

## Outcome

The last day is closed with its leftovers settled and a summary written, and today starts with a plan that has read that summary.

## Edge cases

- However many days were skipped, only the last day started is settled: a skipped week gets one pass, not seven.
- A task left without a choice rolls over, and a push without a date goes to tomorrow.
- No reflection is written for a day closed this way; nobody sees its goodnight.
