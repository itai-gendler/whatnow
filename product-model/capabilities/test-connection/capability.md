---
domain: general
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/httpapi/settings.go#Server.testConnection
- kind: code
  role: implementation
  target: web/src/routes/settings/+page.svelte
- kind: code
  role: implementation
  target: web/src/routes/welcome/+page.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Test connection

Check the chosen provider answers, before relying on it: Test connection in Settings, and the test step
of first-run setup, which runs on arrival. It sends one tiny request to the main model and one to the
light model, so a mistyped light model shows here rather than as tidy-ups that quietly fail.
