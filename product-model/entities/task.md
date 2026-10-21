---
domain: today
relations:
  - entity: blocker
    verb: has
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Task
  - kind: code
    role: implementation
    target: internal/service/tasks.go
  - kind: code
    role: implementation
    target: internal/facts/facts.go#Eligible
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-05-whatnow-design.md
---

# Task

Something the person means to do, at no fixed time. Tasks come from captured notes and brain dumps,
from the task form, from the assistant, and from picked Jira tickets and Review Queue pull requests. An
open task that isn't put off past today is eligible: plans, What now and the unplanned tray draw on
eligible tasks only.

## Information kept

- **Title** — short and concrete, in the person's words where possible
- **Notes** — details that don't fit the title; links in them open in a new tab
- **As captured** — the person's original words, which no edit changes
- **Size** — S, M or L, or none
- **Energy** — low, med or high, or none
- **Feeling** — a few words on how the person feels about it, such as "dreading it"
- **Due** — the date it is due, or none
- **Not before** — the first day it can be done, or none; a push sets it
- **Refs** — ticket keys and links taken from its text, or the ticket or pull request it was picked from
- **Added by** — the person or the assistant
- **Times pushed** — how often it has been pushed, leaving out pushes that were undone

## States

### Open

Still to do. Only an open task can be planned, picked, pushed, dropped or finished.

### Done

Finished. It leaves today's tiers at once and counts toward the day's win line.

### Dropped

Let go without doing it. All tasks lists it under Dropped, where it can be restored.
