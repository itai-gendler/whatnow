---
relations:
  - entity: plan
    verb: has
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Day
  - kind: code
    role: implementation
    target: internal/service/days.go
  - kind: spec
    role: intent
    target: docs/superpowers/specs/2026-10-06-whatnow-reflection-design.md
---

# Day

One calendar day the person started with Good morning. It holds the pace they chose and, once wrapped
up, what is left for the next morning.

## Information kept

- **Date** — the calendar date, in the person's time zone
- **Pace** — one of five levels: running on fumes, gentle, steady, full steam, go hard
- **Mood** — the optional answer to "How are you feeling?"
- **Started** — when the day was started
- **Note for tomorrow** — the optional note left at wrap-up
- **Summary** — the planner's plain notes on the day, written by the light model at wrap-up and read by later plans; never shown to the person
- **Reflection** — the day told to the person, in the assistant's voice, written from the summary

## States

### Started

The day has a pace and a plan, and the plan changes as the day does.

### Wrapped

The day is over. Its plan never changes again, and Today shows the day's-done card instead of the tiers.
