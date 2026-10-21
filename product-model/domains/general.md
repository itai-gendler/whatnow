---
references:
  - kind: code
    role: implementation
    target: web/src/routes/settings/+page.svelte
---

# General

The General section of Settings: the model connection, the person's style and About me, the working
day, nudges, remote access, the look, and deleting everything.

## Boundary

General owns the settings document, the connection test, notification permission and deleting all
data. It does not own integration setup, which is the Integrations section.
