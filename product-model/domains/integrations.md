---
references:
  - kind: code
    role: implementation
    target: web/src/routes/settings/integrations/+page.svelte
---

# Integrations

Google Calendar, Jira and Review Queue: setting them up, pulling from them, and what they skip.

## Boundary

Integrations owns each integration's setup, its pulls and picks, and its skipped items. It does not own
the tasks and events a pull brings in once they are on the list; those are changed like any others.
