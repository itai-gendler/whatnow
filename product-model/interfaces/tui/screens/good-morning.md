---
entities:
  - entity: task
    shows: [Title]
    collects: [As captured]
  - entity: day
    collects: [Pace, Mood]
  - entity: plan
    shows: [Opening, Tiers]
  - entity: event
    shows: [Title, Starts]
  - entity: calendar
    shows: [Name]
references:
  - kind: code
    role: implementation
    target: internal/tui/morning.go
  - kind: code
    role: implementation
    target: internal/tui/calendar.go
  - kind: code
    role: implementation
    target: internal/tui/jira.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-07-whatnow-tui-morning-design.md
---

# Good morning

The terminal's morning ritual, one step at a time: reconcile, brain dump, a Calendar step and a ticket
step when those integrations are on, pace and mood, and the plan reveal.
