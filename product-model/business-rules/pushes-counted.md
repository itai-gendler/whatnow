---
appliesTo:
- type: capability
  id: push-task
- type: capability
  id: edit-task
- type: capability
  id: chat-with-assistant
- type: entity
  id: task
  effect: changes
  facts:
  - Times pushed
references:
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.PushTask
- kind: code
  role: implementation
  target: internal/service/tasks.go#Service.PushCounts
- kind: code
  role: implementation
  target: internal/agent/tools.go
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Only a push puts a task off and counts

Pushing sets a task's not-before date and adds one to its push count. Editing the not-before date in
the task sheet is an ordinary edit that counts nothing, and the assistant always pushes rather than
edits, so its pushes count. Undone pushes don't count.

## Rationale

A task pushed again and again says something about it; plans see the count.
