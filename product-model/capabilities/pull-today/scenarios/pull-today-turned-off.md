---
kind: validation
routes:
  web: Web UI
steps:
- text: The Google Calendar integration is off or has no Calendar
  kind: condition
  entities:
  - {entity: google-calendar-integration, effect: reads, facts: ['On']}
  - {entity: calendar, effect: reads, facts: []}
  contexts:
    web:
      place: web::integrations
- text: The User looks for Pull today on the card
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
- text: The Product keeps Pull today disabled and refuses any pull
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::integrations
---

# No pull while the integration is off

## Trigger

The Google Calendar integration is off, or has no calendar saved.

## Outcome

The morning offers no Google Calendar pull, the card's Pull today is disabled, and a pull is refused.
