---
singleton: true
domain: general
references:
  - kind: code
    role: implementation
    target: internal/settings/settings.go#Settings
  - kind: code
    role: implementation
    target: internal/settings/keys.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-web-ui-settings-design.md
---

# Settings

How whatnow is set up for the person: which model it uses, how the assistant sounds, when the working
day ends, which nudges come, how it looks and who else may open it.

## Information kept

- **Provider** — Anthropic or OpenAI-compatible; none until set up
- **API key** — the provider's key, kept in the system keychain, or found in ANTHROPIC_API_KEY or OPENAI_API_KEY
- **Main model** — runs plans, What now, triage suggestions and chat; claude-sonnet-5-5 by default on Anthropic
- **Light model** — runs tidy-up, day summaries and reflections; claude-haiku-4-5 by default on Anthropic
- **Base URL** — the address of an OpenAI-compatible server, such as Ollama or OpenRouter
- **Assistant style** — how the assistant talks, up to 500 characters
- **About me** — how the person works, up to 1000 characters
- **End of day** — when the working day ends; 17:30 unless changed
- **Event alerts** — how many minutes before an event its nudge comes, from 1 to 60; 10 unless changed
- **Before each event** — whether the before-event nudge is on; on unless turned off
- **When an event ends** — whether the event-end nudge is on; on unless turned off
- **Late in the day** — whether the late-day nudge is on; on unless turned off
- **Look** — Sticker, Dream of the 90s, Neon Nights, Terminal, Paper or Vaporwave
- **Allowed hosts** — hostnames besides this machine that can open the web UI, such as its Tailscale name
- **Setup finished** — set once first-run setup is finished or put off for later
