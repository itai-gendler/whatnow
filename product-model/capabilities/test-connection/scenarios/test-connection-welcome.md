---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User arrives at the connection test
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The Product tests the main and light models at once
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Provider, API key, Main model, Light model]}
  contexts:
    web:
      place: web::welcome
- text: The Product says Connected and lets the User go on
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
---

# Test the connection in first-run setup

## Trigger

The person saved a key in Welcome.

## Outcome

Next turns on once the test passes; on a failure the error shows with Try again, and Back or Set up later are the ways out.
