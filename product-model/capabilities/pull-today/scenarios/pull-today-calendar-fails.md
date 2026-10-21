---
kind: edge
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User pulls today's meetings from the Google Calendar card, or the Calendar step in the terminal
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: One Calendar's feed can't be fetched or read
  kind: condition
  entities:
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: The Product adds and moves meetings from the other calendars, and removes no Event at all, since the missing
    ones can't be told from cancelled ones
  kind: product
  actor: user
  entities:
  - {entity: event, effect: creates, facts: [Title, Starts, Ends, Pulled from]}
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
- text: The Product shows the failed Calendar's error in place of its group, naming it and never its address, with
    Retry
  kind: product
  entities:
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
    tui:
      place: tui::good-morning
---

# Pull when one calendar can't be read

## Trigger

One calendar's address is wrong, Google is unreachable, or the feed takes over 30 seconds.

## Outcome

The other calendars' meetings are in; nothing is removed; the failed calendar shows its error with Retry.

## Edge cases

- Errors read like "Google said 404, check the address", "couldn't reach Google" or "Google took too long to answer".
- One malformed meeting is skipped rather than failing its calendar.
