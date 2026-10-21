---
references:
  - kind: code
    role: implementation
    target: web/src/routes/(app)/+page.svelte
---

# Today

The home page of the web UI and the day view of the terminal: today's plan, What now, and the tiers a
task sits in.

## Boundary

Today owns seeing the day, asking what now and passing on a pick, moving a task between tiers, and
replanning. It does not own the task actions every task card offers (finish, push, drop, edit), which
All tasks offers too, nor chat, capture or undo, which follow the person onto every page.
