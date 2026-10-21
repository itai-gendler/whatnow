---
kind: primary
routes:
  web: Web UI
steps:
- text: The User edits the Connection, You, working hours, Nudges or Remote access sections of the General page
  kind: actor
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Provider, Assistant style, About me, End of day]}
  contexts:
    web:
      place: web::general
- text: The User chooses Save
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::general
- text: The Product saves a newly typed API key to the system keychain, then saves the rest of the Settings
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Provider, API key, Main model, Light model, Base URL, Assistant
        style, About me, End of day, Event alerts, Before each event, When an event ends, Late in the day, Allowed
        hosts]}
  contexts:
    web:
      place: web::general
---

# Save general settings

## Trigger

The person wants plans to know their focus peaks before lunch, and their working day to end at 17:30.

## Outcome

Every later plan, pick and chat reads the new settings.

## Edge cases

- The key field shows only "saved", "from env" or "not set", never the key.
- If the second write fails, the key note is refreshed and typed edits stay in the form.
