---
entities:
  - entity: day
    shows: [Date, Pace, Reflection, Note for tomorrow]
  - entity: plan
    shows: [Tiers]
  - entity: task
    shows: [Title]
  - entity: blocker
    shows: [Blocking task]
  - entity: event
    shows: [Title, Starts]
  - entity: settings
    shows: [End of day]
  - entity: change
    shows: [What changed]
references:
  - kind: code
    role: implementation
    target: internal/tui/view.go
  - kind: code
    role: implementation
    target: internal/tui/snapshot.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-tui-design.md
---

# Today

The terminal's day view: the date, the done count and the pace, the day strip, and the task list by
tier with a "not planned" group, where ⛓ marks a task waiting on an open blocker. Before the day starts
it shows the good-morning card; once the day is wrapped, the goodnight card with the reflection and the
note for tomorrow.
