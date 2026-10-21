---
entities:
  - entity: task
    shows: [Title, Notes, Size, Energy, Feeling, Due, Not before, As captured]
    collects: [Title, Notes, Size, Energy, Feeling, Due, Not before]
  - entity: blocker
    shows: [Blocking task]
    collects: [Blocking task]
references:
  - kind: code
    role: implementation
    target: web/src/lib/components/TaskEditor.svelte
  - kind: code
    role: implementation
    target: web/src/lib/taskForm.ts
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Task sheet

The sheet that opens over Today or All tasks to add a new task or edit one: its fields, what it is
blocked by, and, for an edited task, its words as captured.
