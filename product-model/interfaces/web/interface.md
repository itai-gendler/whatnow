---
type: web
actors: [user]
entryPoints:
  - web: http://127.0.0.1:7777/
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-05-whatnow-web-ui-today-design.md
  - kind: code
    role: implementation
    target: internal/httpapi/server.go
  - kind: code
    role: implementation
    target: web/src/routes/+layout.svelte
---

# Web UI

The browser app whatnow serves on the person's own machine, by default at 127.0.0.1:7777: Today, the
Good morning and Wrap up rituals, All tasks, Settings and first-run setup. It has no sign-in. Every open
tab refreshes when something changes, wherever the change was made.
