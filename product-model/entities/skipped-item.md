---
domain: integrations
references:
  - kind: code
    role: implementation
    target: internal/integrations/saved.go#Skip
  - kind: code
    role: implementation
    target: internal/integrations/runner.go#Runner.Skip
---

# Skipped item

A recurring meeting, Jira ticket or pull request the person chose never to see again. Pulls leave it
out until it is brought back in settings.

## Information kept

- **Key** — its identity in the integration: the meeting series, the ticket key or the pull request
- **Title** — what it was called when it was skipped
