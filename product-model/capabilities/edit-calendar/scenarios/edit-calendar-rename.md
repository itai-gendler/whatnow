---
kind: primary
routes:
  web: Web UI
steps:
- text: The User renames a Calendar row, leaves its address blank, and saves
  kind: actor
  actor: user
  entities:
  - {entity: calendar, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::integrations
- text: The Product saves the new name and keeps the saved address
  kind: product
  actor: user
  entities:
  - {entity: calendar, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web::integrations
---

# Rename a calendar

## Trigger

The person wants Personal listed as Home.

## Outcome

The calendar is called Home, and its address is unchanged.
