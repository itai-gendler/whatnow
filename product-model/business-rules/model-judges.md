---
appliesTo:
- type: capability
  id: replan-day
- type: capability
  id: start-day
- type: capability
  id: ask-what-now
references:
- kind: code
  role: implementation
  target: internal/facts/facts.go#Compute
- kind: code
  role: implementation
  target: internal/prompt/facts.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Facts reach the model as notes, never as filters

whatnow works out free time until the end of day, blocked tasks, not-before and due dates, and push
counts, and hands them to the model as notes on each task, such as "blocks a must" or "pushed 4
times". Ordering, tiering, pacing and reading how the person feels are the model's. Code rejects only
what is impossible.
