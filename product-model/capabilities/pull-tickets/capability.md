---
domain: integrations
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Pull
- kind: code
  role: implementation
  target: internal/integrations/jira/jira.go
- kind: code
  role: implementation
  target: internal/integrations/reviewqueue/reviewqueue.go
- kind: code
  role: implementation
  target: web/src/lib/components/TicketPicker.svelte
- kind: code
  role: implementation
  target: internal/tui/jira.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-15-whatnow-review-queue-design.md
---

# Pull tickets

Offer work to pick from: Jira tickets found by the person's own search, or the pull requests a running
Review Queue ranks for their review. Pull from the brain dump step, Pull on the settings card,
or the ticket step of the terminal's morning. Nothing is written on pull and nothing starts ticked, and
tickets already on the list aren't offered again.
