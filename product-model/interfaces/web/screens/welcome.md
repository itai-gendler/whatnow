---
entities:
  - entity: settings
    shows: [Provider, Main model, Light model, Base URL]
    collects: [Provider, API key, Main model, Light model, Base URL, Assistant style, About me]
entryPoints:
  - web: /welcome
references:
  - kind: code
    role: implementation
    target: web/src/routes/welcome/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/welcome.ts
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Welcome

First-run setup, one step at a time: provider and models, the API key, a connection test, About you,
integrations, nudges, and a last step that starts the first day. whatnow opens here until setup is
finished or put off, as long as no provider is saved.
