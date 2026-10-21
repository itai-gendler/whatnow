---
kind: validation
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The Day is wrapped
  kind: condition
  unattended: true
  entities:
  - {entity: day, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product makes no new Plan for it, whatever asks
  kind: product
  entities:
  - {entity: plan, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Never replan a wrapped day

## Trigger

Something that would warrant a replan happens after the day is wrapped.

## Outcome

The wrapped day's last plan stays as it was.
