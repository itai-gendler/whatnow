---
kind: edge
routes:
  web: Web UI
steps:
- text: The User captures a note
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::today
- text: The Product saves the note at once as an open Task titled with its first line, keeping the words as captured
  kind: product
  actor: user
  entities:
  - {entity: task, effect: creates, to: Open, facts: [Title, As captured, Added by]}
  contexts:
    web:
      place: web::today
- text: The User edits the new Task before tidy-up finishes
  kind: actor
  actor: user
  entities:
  - {entity: task, effect: changes, facts: [Title]}
  contexts:
    web:
      place: web::task
- text: Tidy-up finds the Task edited since capture and leaves it as the User left it
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: []}
  contexts:
    web:
      place: web::task
---

# Leave a note alone that changed before tidy-up finished

## Trigger

The person captures a note and edits it in the task sheet before tidy-up has finished.

## Outcome

The task stays exactly as the person left it; tidy-up quietly changes nothing.

## Edge cases

- A note deleted before tidy-up finishes is left alone the same way.
