---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User opens Today
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product shows the latest Plan with each open Task in its tier and order
  kind: product
  entities:
  - {entity: plan, effect: reads, facts: [Tiers, Rough plan]}
  - {entity: task, effect: reads, facts: [Title, Size, Energy, Feeling]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product lists each eligible Task the Plan leaves out in the unplanned tray
  kind: product
  entities:
  - {entity: plan, effect: reads, facts: [Tiers]}
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product places each of today's Event entries on the day strip, with the now line and the end-of-work
    mark
  kind: product
  entities:
  - {entity: event, effect: reads, facts: [Title, Starts, Ends]}
  - {entity: settings, effect: reads, facts: [End of day]}
  - {entity: day, effect: reads, facts: [Started]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product counts each Task done today and each Event already over into the win line
  kind: product
  entities:
  - {entity: task, effect: reads, facts: []}
  - {entity: event, effect: reads, facts: [Ends]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# See the planned day

## Trigger

The person looks at whatnow during a started day.

## Outcome

Today shows the plan's open tasks by tier, the eligible tasks the plan leaves out, today's events and the win line.

## Edge cases

- A plan code made while the model was out carries a "rough plan, model was out" tag.
- A card linked by blockers shows "⛓ waits on N" or "unblocks N", counting open tasks only.
- An event with no end is drawn as 30 minutes.
