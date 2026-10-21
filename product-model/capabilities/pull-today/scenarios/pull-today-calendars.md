---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User pulls Google Calendar from the brain dump step
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Google Calendar integration is on and has at least one Calendar
  kind: condition
  entities:
  - {entity: google-calendar-integration, effect: reads, facts: ['On']}
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product fetches each Calendar's feed for today, leaving out date-only entries, meetings the person declined,
    and skipped series
  kind: product
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: [Name, Secret address]}
  - {entity: skipped-item, effect: reads, facts: [Key]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product adds each new meeting as an Event
  kind: product
  actor: user
  entities:
  - {entity: event, as: new, effect: creates, facts: [Title, Starts, Ends, Pulled from]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product moves or renames each pulled Event whose meeting moved or was renamed in the feed, over any
    hand edit
  kind: product
  actor: user
  entities:
  - {entity: event, as: moved, effect: changes, facts: [Title, Starts, Ends]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product removes each of today's pulled Event entries the feed no longer has
  kind: product
  actor: user
  entities:
  - {entity: event, as: gone, effect: removes}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product lists the meetings by calendar with a count, each with ×
  kind: product
  entities:
  - {entity: event, as: new, effect: reads, facts: [Title, Starts]}
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Pull today's meetings into the morning

## Trigger

During the brain dump, the person wants today's meetings in before planning.

## Outcome

Today's meetings are events on the strip, grouped by calendar in the results, and the plan made next sees them.

## Edge cases

- A meeting on two calendars lands once.
- A meeting the person removed stays removed, unless it disappears from the feed and comes back.
- A pull later in the day doesn't replan on its own; Replan picks the new events up.
