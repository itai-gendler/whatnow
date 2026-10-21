---
domain: today
references:
  - kind: code
    role: implementation
    target: internal/service/blockers.go
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Blocker
---

# Blocker

One task waiting on another. A task can wait on several tasks. Only an open blocking task holds its
waiting task back: once it is done or dropped, the waiting task is free to start.

## Information kept

- **Blocking task** — the task that has to be finished first
