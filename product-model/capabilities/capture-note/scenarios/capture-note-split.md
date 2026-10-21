---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User captures one note naming several things to do
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: The Product saves the note at once as an open Task titled with its first line, keeping the words as captured
  kind: product
  actor: user
  entities:
  - {entity: task, as: note, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up keeps the note's Task as the FLEX1-666 work, due today, with the feeling "feels difficult" and its
    ticket key
  kind: product
  actor: user
  entities:
  - {entity: task, as: note, effect: changes, facts: [Title, Due, Feeling, Refs]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up adds the pubsub research and the FLEX1-420 review as two more open Task entries, each keeping the
    note as captured
  kind: product
  actor: user
  entities:
  - {entity: task, as: research, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  - {entity: task, as: review, effect: creates, to: Open, facts: [Title, As captured, Added by, Refs]}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
- text: Tidy-up adds a Blocker so the FLEX1-666 Task waits on the research
  kind: product
  actor: user
  entities:
  - {entity: blocker, effect: creates, facts: [Blocking task]}
  - {entity: task, as: note, effect: reads, facts: []}
  - {entity: task, as: research, effect: reads, facts: []}
  contexts:
    web:
      place: web::today
    tui:
      place: tui::today
---

# Split one note into several tasks with a blocker

## Trigger

The person captures "do FLEX1-666 today, it feels difficult and needs pubsub research first; also review FLEX1-420".

## Outcome

One note became three tasks, with the research blocking FLEX1-666, all in one change.

## Edge cases

- A blocker never closes a loop; tidy-up that would make one changes nothing.
