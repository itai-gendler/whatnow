---
relations:
  - entity: task
    verb: places
    cardinality: many-to-many
references:
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Plan
  - kind: code
    role: implementation
    target: internal/planner/plan.go
  - kind: code
    role: implementation
    target: internal/planner/move.go
---

# Plan

One version of a day's plan. Each change worth replanning adds a version; a version is never edited,
and Today shows the latest one.

## Information kept

- **Version** — numbered from 1 within its day
- **Made because** — the morning start, a pace change, another change worth replanning, the assistant, the Replan button, or a task moved by hand
- **Reason** — what changed, in a few words
- **Opening** — two or three sentences in the assistant's voice, shown first in chat
- **Tiers** — each planned task in must, should or could, in suggested order, with a one-line rationale
- **Rough plan** — set when code made the plan because the model couldn't
