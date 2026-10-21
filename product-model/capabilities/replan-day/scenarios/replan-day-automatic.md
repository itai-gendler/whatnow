---
kind: automatic
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: An edit makes a Task due today, drops or deletes a must, or adds or removes a Blocker on a must
  kind: condition
  unattended: true
  entities:
  - {entity: task, effect: reads, facts: [Due]}
  - {entity: blocker, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The main model plans the Day again, told what changed
  kind: product
  entities:
  - {entity: day, effect: reads, facts: [Pace, Mood]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product saves the new Plan version with the reasons
  kind: product
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Replan when something warrants it

## Trigger

A change lands that matters to the plan, such as a task becoming due today or a must being dropped, from either UI, tidy-up or the assistant.

## Outcome

Both UIs show the new plan version; the opening says what changed.

## Edge cases

- Changes that land while a replan runs are folded into one more replan.
- Undoing such a change is itself a reason to replan.
- Finishing a must, or adding a task not due today, doesn't replan.
