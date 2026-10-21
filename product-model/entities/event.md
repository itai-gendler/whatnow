---
domain: today
references:
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Event
  - kind: code
    role: implementation
    target: internal/service/events.go
  - kind: code
    role: implementation
    target: internal/service/sync.go
---

# Event

Anything at a fixed time: a standup, a 1:1, a dentist appointment. Events come from captured notes, from
the assistant, and from Google Calendar pulls. Today's events sit on the day strip, take up free time in
planning, and set off nudges.

## Information kept

- **Title** — what it is
- **Starts** — when it starts
- **Ends** — when it ends, if it has a set end; an event with none counts as 30 minutes
- **As captured** — the note it came from, when tidy-up made it
- **Pulled from** — for a pulled event, the integration and the event's identity in the calendar feed
