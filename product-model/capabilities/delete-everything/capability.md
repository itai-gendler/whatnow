---
domain: general
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/httpapi/settings.go#Server.deleteData
- kind: code
  role: implementation
  target: web/src/lib/components/DangerZone.svelte
- kind: code
  role: implementation
  target: internal/store/wipe.go#Wipe
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Delete everything

Start over: Delete everything in the Danger zone of Settings → General, once the field next to it reads
"delete everything". Every task, event, day, plan, chat and summary, the settings, both saved API keys
and the integrations' saved addresses and tokens are deleted. There is no undo.
