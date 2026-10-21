---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses + Add under Calendars, types Work and the secret address, and saves
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
- text: The Product adds the Calendar, keeping its secret address in the system keychain
  kind: product
  actor: user
  entities:
  - {entity: calendar, effect: creates, facts: [Name, Secret address]}
  - {entity: google-calendar-integration, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
---

# Add a calendar by its secret address

## Trigger

The person wants their Work calendar's meetings pulled.

## Outcome

Work is listed under Calendars with its address shown only as saved.
