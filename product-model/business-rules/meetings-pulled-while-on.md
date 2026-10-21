---
appliesTo:
- type: capability
  id: pull-today
- type: entity
  id: event
  effect: creates
  facts:
  - Pulled from
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Pull
- kind: code
  role: implementation
  target: internal/integrations/runner.go#View.On
---

# Meetings are pulled only while Google Calendar is on

A pulled meeting comes into whatnow only while the Google Calendar integration is on and has a
calendar; turned off, it keeps its calendars and pulls nothing.
