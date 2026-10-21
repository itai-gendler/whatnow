---
domain: today
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/+page.svelte
- kind: code
  role: implementation
  target: web/src/lib/plan.ts#tiers
- kind: code
  role: implementation
  target: internal/planner/today.go#Planner.Today
- kind: code
  role: implementation
  target: internal/tui/view.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-tui-design.md
---

# View today

See where today stands: the plan's open tasks by tier, the unplanned tray, today's events on the day
strip, and what got done. A task finished, dropped, deleted or pushed past today leaves its tier at
once, without waiting for a replan.
