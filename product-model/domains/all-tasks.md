---
references:
  - kind: code
    role: implementation
    target: web/src/routes/(app)/tasks/+page.svelte
---

# All tasks

The list of every task, whatever its state, with its filters.

## Boundary

All tasks owns browsing every task and restoring dropped ones. It does not own planning: which tasks
sit in today's tiers belongs to Today.
