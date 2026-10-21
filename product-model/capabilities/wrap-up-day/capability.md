---
availability:
- place: web
references:
- kind: code
  role: implementation
  target: internal/planner/close.go#Planner.WrapUp
- kind: code
  role: implementation
  target: internal/planner/review.go#Planner.WrapReview
- kind: code
  role: implementation
  target: internal/planner/reflection.go
- kind: code
  role: implementation
  target: web/src/routes/(ritual)/wrap/+page.svelte
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-reflection-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Wrap up the day

End the day with Wrap up: see what got done, decide what happens to each unfinished task, leave a note
for tomorrow, and read a goodnight reflection. Wrap up shows in the header from an hour before the end
of day; Wrap up early is there any time. The triage is one change; wrapping can't be
undone. In the terminal, a banner says to wrap up in the browser.
