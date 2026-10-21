---
domain: general
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/routes/settings/+page.svelte
- kind: code
  role: implementation
  target: web/src/lib/components/ThemePicker.svelte
- kind: code
  role: implementation
  target: web/src/routes/welcome/+page.svelte
- kind: code
  role: implementation
  target: internal/settings/settings.go#Settings.Validate
- kind: code
  role: implementation
  target: internal/httpapi/settings.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Change general settings

Shape whatnow in Settings → General: the provider, API key and models; Assistant style and About me;
the end of day and how many minutes before an event its nudge comes; which nudges come; Remote access;
and the look. One Save writes the key first, then the rest; the look is saved the moment it is picked.
The provider, models, key, Assistant style and About me are also set in first-run setup.
