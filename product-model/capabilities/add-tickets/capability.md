---
domain: integrations
availability:
- place: web
- place: tui
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Add
- kind: code
  role: implementation
  target: web/src/lib/components/TicketPicker.svelte#add
- kind: code
  role: implementation
  target: internal/tui/jira.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
---

# Add picked tickets

Turn the ticked tickets into tasks: Add N under the pick list, or enter in the terminal's ticket step.
A picked ticket is a one-time copy: nothing syncs back to Jira or GitHub, and closing it there never
closes the task. Its task skips tidy-up and keeps size and energy blank, so it waits in the unplanned
tray until the person says more.
