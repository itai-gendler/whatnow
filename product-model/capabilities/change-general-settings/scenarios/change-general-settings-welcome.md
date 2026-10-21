---
kind: alternate
routes:
  web: Web UI
steps:
- text: The User picks Anthropic or OpenAI-compatible, checking the main and light models, with a base URL for an
    OpenAI-compatible server
  kind: actor
  actor: user
  entities:
  - {entity: settings, effect: reads, facts: [Provider, Main model, Light model]}
  contexts:
    web:
      place: web::welcome
- text: The User enters the API key, or keeps the one found in the environment, and goes on
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::welcome
- text: The Product saves the key to the system keychain and the provider and models to the Settings
  kind: product
  actor: user
  entities:
  - {entity: settings, effect: changes, facts: [Provider, API key, Main model, Light model, Base URL]}
  contexts:
    web:
      place: web::welcome
---

# Choose the model and key in first-run setup

## Trigger

On a fresh install, the person picks a provider in Welcome.

## Outcome

The provider, models and key are saved, and the connection test runs next.

## Edge cases

- OpenAI-compatible models have no defaults; Next stays off until both are filled in.
- A key found in ANTHROPIC_API_KEY or OPENAI_API_KEY is named on the step, with a link to use a different one.
