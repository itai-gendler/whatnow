---
singleton: true
domain: integrations
relations:
  - entity: skipped-item
    verb: skips
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: internal/integrations/reviewqueue/reviewqueue.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-15-whatnow-review-queue-design.md
---

# Review Queue integration

The Review Queue setup: where the person's running Review Queue is, and the lowest score a pull
request needs to be offered. It pulls only while it is on and has an address.

## Information kept

- **On** — whether it is turned on; turning it off keeps its fields
- **Address** — where Review Queue runs, such as http://localhost:5173
- **Minimum score** — pull requests scoring below it are not offered; blank offers all
