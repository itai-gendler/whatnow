---
domain: general
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/components/NotifyPermission.svelte
- kind: code
  role: implementation
  target: web/src/routes/welcome/+page.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Turn on notifications

Let nudges arrive as system notifications: Turn on notifications, in Settings or on the Nudges step
of first-run setup, asks the browser for permission. Without it, nudges show in the page instead.
