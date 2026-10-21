---
appliesTo:
- type: capability
  id: change-general-settings
- type: capability
  id: change-integration-settings
- type: capability
  id: add-calendar
- type: capability
  id: remove-calendar
- type: capability
  id: delete-everything
references:
- kind: code
  role: implementation
  target: internal/settings/keys.go
- kind: code
  role: implementation
  target: internal/integrations/saved.go#DeleteSecrets
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Save
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# Keys and secret addresses live in the system keychain

API keys, Google Calendar secret addresses and the Jira token are kept in the system keychain, never in
whatnow's database, and are shown only as saved or not set. Deleting a calendar row deletes its
address from the keychain, and Delete everything deletes them all, apart from keys read from the
environment.
