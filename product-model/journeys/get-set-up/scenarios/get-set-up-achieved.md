---
kind: primary
result: achieved
routes:
  web: Web UI
steps:
- text: The User picks a provider and its models on Welcome, enters the API key, and goes on
  kind: actor
  actor: user
  capability: change-general-settings
  entities:
  - {entity: settings, effect: changes, facts: [Provider, API key, Main model, Light model, Base URL]}
  contexts:
    web:
      place: web::welcome
- text: The Product tests the connection at once and says Connected
  kind: product
  actor: user
  capability: test-connection
  entities:
  - {entity: settings, effect: reads, facts: [Provider, API key, Main model, Light model]}
  contexts:
    web:
      place: web::welcome
- text: The User goes on through About you, integrations and nudges, and chooses Next
  kind: actor
  actor: user
  capability: finish-setup
  entities:
  - {entity: settings, effect: changes, facts: [Setup finished]}
  contexts:
    web:
      place: web::welcome
- text: The User chooses to start the first morning, and the Product opens Good morning
  kind: actor
  actor: user
  capability: start-day
  entities: []
  contexts:
    web:
      place: web::good-morning
- text: The User dumps what's on their plate and picks a pace
  kind: actor
  actor: user
  capability: start-day
  entities: []
  contexts:
    web:
      place: web::good-morning
- text: The Product starts the Day
  kind: product
  actor: user
  capability: start-day
  entities:
  - {entity: day, effect: creates, to: Started, facts: [Date, Pace, Mood, Started]}
  contexts:
    web:
      place: web::good-morning
- text: The Product saves the first Plan and reveals it
  kind: product
  actor: user
  capability: start-day
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  contexts:
    web:
      place: web::good-morning
---

# Set up whatnow and plan the first day

## Trigger

The person opens whatnow for the first time, with no provider saved.

## Outcome

Setup is finished and the first day is planned; Welcome never opens again.
