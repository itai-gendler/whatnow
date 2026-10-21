---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User chooses × on a pulled recurring Event, then Always skip
  kind: actor
  actor: user
  entities:
  - {entity: event, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product removes today's Event in an undoable step
  kind: product
  actor: user
  entities:
  - {entity: event, effect: removes}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product adds the series to the Google Calendar integration's skipped list as a Skipped item
  kind: product
  actor: user
  entities:
  - {entity: skipped-item, effect: creates, facts: [Key, Title]}
  - {entity: google-calendar-integration, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Always skip a recurring meeting

## Trigger

A recurring meeting in the pull, such as a daily blockout, never needs to be in whatnow.

## Outcome

Today's occurrence is gone, the series is on the skipped list, and later pulls leave it out.

## Edge cases

- Undoing it brings today's occurrence back; the series stays skipped until brought back.
- In the terminal, removing a recurring meeting asks the same: just today, or always.
