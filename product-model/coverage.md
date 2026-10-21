---
scope: The whatnow program, its web UI and its terminal UI, with their planning, assistant, integration
  and settings code.
method: Static reading of the Go packages and the web client at the pinned commit, with the design
  specifications and tests as leads.
covered:
  - description: Write path for tasks, blockers, events, days, plans and undo.
    paths: [internal/service/, internal/domain/]
  - description: Planning, What now, reviews, wrap-up and the replan watcher.
    paths: [internal/planner/, internal/facts/, internal/prompt/]
  - description: Chat agent loop and its tools.
    paths: [internal/agent/agent.go, internal/agent/tools.go, internal/agent/instructions.go]
  - description: Tidy-up of captured notes.
    paths: [internal/cleanup/]
  - description: Integration contract, runner and the three built-in integrations.
    paths: [internal/integrations/]
  - description: Settings document and keychain keys.
    paths: [internal/settings/]
  - description: HTTP API the web client calls.
    paths: [internal/httpapi/]
  - description: Process wiring shared by the server and the terminal UI.
    paths: [internal/app/]
  - description: Terminal UI.
    paths: [internal/tui/]
  - description: Web client pages and logic modules.
    paths: [web/src/routes/, web/src/lib/]
exclusions:
  - description: Model provider clients and their fake.
    paths: [internal/llm/]
  - description: Database access, migrations and the live event hub.
    paths: [internal/store/, internal/stream/, internal/jsonschema/]
  - description: Static file serving and command-line entry point, demo clock and test build.
    paths: [internal/web/, cmd/whatnow/]
  - description: Release, packaging and developer task runner.
    paths: [packaging/, Justfile]
  - description: Celebration effects, themes and design tokens of the web client and the terminal UI.
    paths: [web/src/lib/celebrate.ts, web/src/lib/cheer.ts, internal/tui/cheer.go, web/src/lib/themes.css, web/src/lib/tokens.css]
  - description: Browser test suite, build configuration and screenshots.
    paths: [web/e2e/, web/static/, web/package.json, web/package-lock.json, web/playwright.config.ts, web/tsconfig.json, web/vite.config.ts, docs/screenshots/]
unmapped:
  - description: Chat context assembly and folding of long chat history.
    paths: [internal/agent/context.go]
limitations: []
---

# Coverage
