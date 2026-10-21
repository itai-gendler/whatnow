---
entities:
  - entity: task
    shows: [Title]
  - entity: event
    shows: [Ends]
  - entity: day
    shows: [Reflection]
    collects: [Note for tomorrow]
entryPoints:
  - web: /wrap
references:
  - kind: code
    role: implementation
    target: web/src/routes/(ritual)/wrap/+page.svelte
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-rituals-design.md
---

# Wrap up

The evening ritual, one step at a time: what got done, what happens to each unfinished task, a note for
tomorrow, and the goodnight reflection.
