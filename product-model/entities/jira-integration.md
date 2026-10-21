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
    target: internal/integrations/jira/jira.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
---

# Jira integration

The Jira setup: where Jira is, the token to reach it, and the search whose tickets are offered as
tasks. It pulls only while it is on and every field is filled.

## Information kept

- **On** — whether it is turned on; turning it off keeps its fields
- **Address** — the Jira server's address, such as https://jira.example.com
- **Personal access token** — kept in the system keychain and shown only as saved
- **Search (JQL)** — the person's own Jira search; nothing is prefilled
