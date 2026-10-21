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
entryPoints:
  - web: /morning
references:
  - kind: code
    role: implementation
    target: web/src/routes/(ritual)/morning/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/components/TriageList.svelte
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Good morning

The morning check-in, one step at a time: reconcile the last day's leftovers when it wasn't wrapped up,
the brain dump with any integrations to pull, pace and mood, and the plan reveal.
