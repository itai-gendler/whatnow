---
kind: primary
routes:
  web: Web UI
steps:
- text: The User chooses remove beside a Calendar row and saves
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
- text: The Product removes the Calendar and deletes its secret address from the system keychain
  kind: product
  actor: user
  entities:
  - {entity: calendar, effect: removes}
  - {entity: google-calendar-integration, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
---

# Stop reading a calendar

## Trigger

The person no longer wants a calendar's meetings in whatnow.

## Outcome

The calendar is gone from the card, and its secret address is gone from the keychain.
