---
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/planner/today.go#Planner.StartDay
- kind: code
  role: implementation
  target: internal/httpapi/days.go#Server.startDay
- kind: code
  role: implementation
  target: internal/planner/review.go#Planner.MorningReview
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.Close
- kind: code
  role: implementation
  target: web/src/routes/(ritual)/morning/+page.svelte
- kind: code
  role: implementation
  target: internal/tui/morning.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-07-whatnow-tui-morning-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Start the day

Start the day with Good morning: reconcile the last day if it was never wrapped up, dump what's on the
person's mind, say the pace and mood, and get a plan in three tiers with an opening in the assistant's
voice. The brain dump is captured and tidied before planning, so its tasks land in the plan rather than
the tray. A day starts once, and starting it can't be undone.
