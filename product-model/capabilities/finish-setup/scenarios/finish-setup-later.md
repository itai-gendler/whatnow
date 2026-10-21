---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User chooses Set up later
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The Product marks setup finished on the Settings as last saved, dropping anything chosen but not yet saved
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Setup finished]}
  contexts:
    web:
      place: web::welcome
- text: The Product opens Today, which goes on to Good morning when nothing is started yet
  kind: product
  entities: []
  contexts:
    web:
      place: web::today
---

# Put setup off for later

## Trigger

The person wants to look around before setting anything up.

## Outcome

whatnow moves on to the day, starting with Good morning if the day hasn't started; Settings has the rest.
