---
kind: automatic
routes:
  web: Web UI
steps:
- text: Two hours before the end of day, an open Task in today's must tier is due today and untouched since midnight,
    and the late-day nudge is on
  kind: condition
  unattended: true
  entities:
  - {entity: task, effect: reads, facts: [Title, Due]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  - {entity: day, effect: reads, facts: []}
  - {entity: settings, effect: reads, facts: [End of day, Late in the day]}
  contexts:
    web:
      place: web
- text: The Product shows one nudge naming the first such Task
  kind: product
  entities:
  - {entity: task, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web
---

# Nudge late in the day about a stalled must

## Trigger

It is two hours before the end of day, and a must due today hasn't been touched today.

## Outcome

The person sees "<title> is due today and hasn't moved yet. Still time."

## Edge cases

- Any edit, push or tick today counts as the task having moved.
