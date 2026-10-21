---
entities:
  - entity: task
    shows: [Title, Size, Energy, Feeling, Notes, Due, Not before]
entryPoints:
  - web: /tasks
references:
  - kind: code
    role: implementation
    target: web/src/routes/(app)/tasks/+page.svelte
  - kind: code
    role: implementation
    target: web/src/lib/tasks.ts
---

# All tasks

Every task, filtered by one of Open, Future, Blocked, Done, Dropped or All, and sorted by
due date, undated last, then newest first.
