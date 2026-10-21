---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/routes/welcome/+page.svelte#finish
- kind: code
  role: implementation
  target: web/src/lib/welcome.ts#welcomeDue
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Finish setup

Close first-run setup: Next on the Nudges step finishes it, and Set up later on any step puts it off,
keeping only what was already saved. Either way whatnow stops opening on Welcome, even in a new
browser. An install that already has a provider never sees Welcome.
