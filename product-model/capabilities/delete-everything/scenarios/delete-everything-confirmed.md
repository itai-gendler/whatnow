---
kind: primary
routes:
  web: Web UI
steps:
- text: The User types "delete everything" in the Danger zone and chooses Delete everything
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product deletes every Task, Blocker, Event, Day, Plan, Chat message and Change
  kind: product
  actor: user
  entities:
  - {entity: task, effect: removes, from: Open}
  - {entity: blocker, effect: removes, with: task}
  - {entity: event, effect: removes}
  - {entity: day, effect: removes, from: Wrapped}
  - {entity: plan, effect: removes, with: day}
  - {entity: chat-message, effect: removes}
  - {entity: change, effect: removes, from: Applied}
  contexts:
    web:
      place: web::general
- text: The Product resets the Settings and the integrations, deleting each Calendar, each Skipped item, and every
    saved key, address and token from the system keychain
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Provider, API key, Main model, Light model, Base URL, Assistant
        style, About me, End of day, Event alerts, Before each event, When an event ends, Late in the day, Allowed
        hosts, Look, Setup finished]}
  - {entity: google-calendar-integration, effect: changes, facts: ['On']}
  - {entity: jira-integration, effect: changes, facts: ['On', Address, Personal access token, Search (JQL)]}
  - {entity: review-queue-integration, effect: changes, facts: ['On', Address, Minimum score]}
  - {entity: calendar, effect: removes}
  - {entity: skipped-item, effect: removes}
  contexts:
    web:
      place: web::general
- text: Every open tab reloads into Welcome
  kind: product
  entities: []
  contexts:
    web:
      place: web::welcome
---

# Start over from nothing

## Trigger

The person wants whatnow back as it was on first install.

## Outcome

Everything is gone, and every open tab reloads into Welcome.

## Edge cases

- A key in ANTHROPIC_API_KEY or OPENAI_API_KEY can't be removed; setup finds it again.
