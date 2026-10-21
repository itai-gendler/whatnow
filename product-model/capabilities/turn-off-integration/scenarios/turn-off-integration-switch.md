---
kind: primary
routes:
  web: Web UI
steps:
- text: The User turns off the switch on the Google Calendar card
  kind: actor
  actor: user
  entities:
  - {entity: google-calendar-integration, effect: reads, facts: ['On']}
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
- text: The Product saves the Google Calendar integration as off, keeping each Calendar
  kind: product
  actor: user
  entities:
  - {entity: google-calendar-integration, effect: changes, facts: ['On']}
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
---

# Turn Google Calendar off

## Trigger

The person is on holiday and doesn't want meetings pulled.

## Outcome

Google Calendar is off: no pull in the morning, no Calendar step in the terminal, and its calendars are kept.
