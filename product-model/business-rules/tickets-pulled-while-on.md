---
appliesTo:
- type: capability
  id: pull-tickets
- type: capability
  id: add-tickets
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.Add
- kind: code
  role: implementation
  target: internal/integrations/runner.go#View.On
---

# Tickets are pulled and added only while their integration is on

Jira and Review Queue offer and add tickets only while they are on and their required fields are
saved; otherwise a pull or add is refused.
