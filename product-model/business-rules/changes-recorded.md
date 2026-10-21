---
appliesTo:
- type: entity
  id: task
  effect: creates
- type: entity
  id: task
  effect: changes
- type: entity
  id: task
  effect: removes
  contexts:
  - place: web::today
  - place: web::chat
  - place: tui::today
- type: entity
  id: event
  effect: creates
- type: entity
  id: event
  effect: changes
- type: entity
  id: event
  effect: removes
  contexts:
  - place: web::today
  - place: web::good-morning
  - place: tui::good-morning
- type: entity
  id: blocker
  effect: creates
- type: entity
  id: blocker
  effect: removes
  contexts:
  - place: web::task
- type: entity
  id: day
  effect: changes
  facts:
  - Pace
  - Mood
- type: entity
  id: change
references:
- kind: code
  role: implementation
  target: internal/service/service.go#record
- kind: code
  role: implementation
  target: internal/service/undo.go#revert
---

# Every edit to tasks, events, blockers and pace is part of one change

Each edit records what the task, event, blocker or day was before and after, in the change it belongs
to: one action of the person's, one assistant reply, one tidy-up or one triage. Undo replays that
record backwards.
