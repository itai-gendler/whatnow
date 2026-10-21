---
appliesTo:
- type: capability
  id: add-tickets
- type: capability
  id: pull-tickets
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Add
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
---

# A picked ticket is a one-time copy

Nothing syncs back either way: finishing the task never touches Jira or GitHub, and a ticket closing
there never closes the task. Its task skips tidy-up, since a ticket is already one clean item, and
keeps size and energy blank.

## Rationale

Finishing and tidying by hand is where the satisfaction and the habit come from, and done in whatnow
rarely means done in Jira.
