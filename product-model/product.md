---
id: whatnow
summary: A day planner for ADHD brains that holds the day loosely in must, should and could tiers, and
  answers "what now?" with one pick and a reason.
category: productivity
tags:
  - adhd
  - planning
  - tasks
  - local-first
authors:
  - name: jameynakama
    url: https://github.com/jameynakama
license: MIT
languages:
  - en
limitations:
  - whatnow is for one person on one machine. There are no accounts, the data stays in one database on
    that machine, and the web UI answers only that machine and the hosts listed under Remote access.
  - Planning, tidy-up, What now and chat need the person's own API key for Anthropic or an
    OpenAI-compatible service. Without one, capture still works and plans and picks come out rough.
  - Integrations only read. Google Calendar, Jira and Review Queue are pulled when the person asks, for
    today only, and nothing is ever written back to them.
  - Nudges come only from an open web page, as a notification or in the page.
  - The terminal UI is a companion. Setup, settings, wrap-up, nudges, editing a task's details and All
    tasks are in the web UI.
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: doc
    role: context
    target: demo.md
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-05-whatnow-design.md
  - kind: code
    role: implementation
    target: internal/app/app.go
  - kind: code
    role: implementation
    target: cmd/whatnow/main.go
---

# whatnow

whatnow is a day planner for people with ADHD. Each morning the person dumps what is on their mind and
says how much they have in them; a language model sorts the dump into tasks and events, notices how they
feel about each, and plans a day in three tiers: must, should and could. During the day they can ask
*what now?* for one pick with a reason, change their pace, and chat with an assistant that changes things
directly and can be undone. In the evening they wrap up: see what got done, decide what happens to
what's left, and leave a note for tomorrow. It runs locally as one program with a web UI and a terminal
UI that stay in step.

## Intent

*Executive function for the rest of us.*

"whatnow is a day planner for ADHD brains. Rather than an hourly schedule, it holds your day loosely:
what you must do, what you should do, and what you could do if there's room. Dump everything on your
plate in whatever words come out. An LLM sorts it into tasks and events, notices how you feel about
them, and plans a day that fits your energy. When you're stuck, ask it *what now?*"
