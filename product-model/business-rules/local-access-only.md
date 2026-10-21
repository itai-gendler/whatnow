---
appliesTo:
- type: context
  context:
    place: web
- type: entity
  id: settings
  facts:
  - Allowed hosts
references:
- kind: code
  role: implementation
  target: internal/httpapi/server.go
- kind: code
  role: implementation
  target: internal/settings/settings.go#Settings.Validate
- kind: doc
  role: intent
  target: README.md
---

# The web UI answers only this machine and the allowed hosts

whatnow's web UI answers requests made to this machine itself, and to the hostnames listed under
Remote access, such as the machine's Tailscale name; any other address is turned away.
