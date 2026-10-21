---
appliesTo:
- type: capability
  id: pull-today
- type: capability
  id: remove-event
- type: capability
  id: skip-pulled-item
references:
- kind: code
  role: implementation
  target: internal/service/sync.go#Service.SyncEvents
- kind: code
  role: implementation
  target: internal/service/events.go#Service.ForgetEvent
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
---

# A meeting the person removed stays removed

A pull updates each pulled meeting to the feed's title and times, over any edit by hand, but never
brings back one the person removed. A meeting the feed drops is removed and forgotten, so if it comes
back to the feed it comes back to whatnow; the same goes for a pull that is undone and pulled again.
