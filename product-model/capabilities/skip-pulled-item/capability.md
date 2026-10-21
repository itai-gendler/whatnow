---
domain: integrations
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Skip
- kind: code
  role: implementation
  target: web/src/lib/components/PullResults.svelte#skip
- kind: code
  role: implementation
  target: web/src/lib/components/TicketPicker.svelte#skip
- kind: code
  role: implementation
  target: internal/tui/calendar.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-integrations-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
---

# Skip a pulled item for good

Never see a recurring meeting, ticket or pull request again: Always skip after × on a recurring meeting
in a pull's results, or × on a ticket in a pick list. It goes on the integration's Skipped list, which
its settings card shows with "bring back".
