---
domain: all-tasks
availability:
- place: web
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/tasks/+page.svelte
- kind: code
  role: implementation
  target: web/src/lib/tasks.ts#listTasks
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Browse all tasks

See every task, whatever its state, on All tasks, filtered by one of Open, Future,
Blocked, Done, Dropped or All. Tasks are sorted by due date, undated last, then newest first, with
their due and not-before dates on the card.
