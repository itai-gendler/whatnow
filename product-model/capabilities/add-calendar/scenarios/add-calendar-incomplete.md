---
kind: validation
routes:
  web: Web UI
steps:
- text: The User saves a new Calendar row missing its name or secret address
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
- text: The Product refuses the whole save and names the row and the missing field
  kind: product
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
---

# Refuse a calendar row missing its name or address

## Trigger

The person saves a new calendar row without a name or a secret address.

## Outcome

Nothing is saved; the card says which row needs what, such as "Calendars row 2 needs a secret address".
