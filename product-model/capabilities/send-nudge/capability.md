---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/lib/nudges.ts
- kind: code
  role: implementation
  target: web/src/lib/live.svelte.ts
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Send a nudge

Nudge the person at the right moments while a whatnow web page is open: before each event, when an
event ends, and late in the day if a must due today hasn't moved. Each kind can be turned off in
Settings. A nudge is a system notification when the browser allows it, and a yellow note in the page
otherwise. Each nudge comes once, and reloading a page never repeats an old one.
