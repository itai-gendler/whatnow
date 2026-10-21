---
entities:
  - entity: settings
    shows: [Provider, Main model, Light model, Base URL, Assistant style, About me, End of day, Event alerts, Before each event, When an event ends, Late in the day, Look, Allowed hosts]
    collects: [Provider, API key, Main model, Light model, Base URL, Assistant style, About me, End of day, Event alerts, Before each event, When an event ends, Late in the day, Look, Allowed hosts]
entryPoints:
  - web: /settings
references:
  - kind: code
    role: implementation
    target: web/src/routes/settings/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/DangerZone.svelte
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# General

The General section of Settings: Connection, You, Day, Nudges and Remote access under one Save, the
Look picker, and the Danger zone. The API key shows only whether it is saved, comes from the
environment, or is not set.
