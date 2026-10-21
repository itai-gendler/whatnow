---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User asks the assistant to break the Q3 report into tiny steps
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves the message under today's date
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: asked, effect: creates, facts: [Date, From, Text]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The main model reads today's tasks, events and plan as they are now, with About me and the last week's day
    summaries
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Title, Notes, Feeling]}
  - {entity: event, effect: reads, facts: [Title, Starts]}
  - {entity: plan, effect: reads, facts: [Tiers]}
  - {entity: day, effect: reads, facts: [Summary]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The assistant adds each step as an open Task added by the assistant
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, Notes, Size, Energy, Added by]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The assistant replans the Day so the steps can land in today's tiers
  kind: product
  actor: user
  entities:
  - {entity: plan, effect: creates, facts: [Version, Made because, Reason, Opening, Tiers, Rough plan]}
  - {entity: day, effect: reads, facts: [Pace]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
- text: The Product saves the reply with each action it took and an Undo, and streams it into every open chat
  kind: product
  actor: user
  entities:
  - {entity: chat-message, as: reply, effect: creates, facts: [Date, From, Text, Changes made]}
  contexts:
    web:
      place: web::chat
    tui:
      place: tui::chat
---

# Break a dreaded task into steps

## Trigger

The person can't face the Q3 report and asks the assistant to help break it into tiny steps.

## Outcome

The report is a handful of small tasks, today's plan has them, and one Undo on the reply would take them all back.

## Edge cases

- A message over 4000 characters is refused.
- The assistant calls tasks by their titles in what it writes.
