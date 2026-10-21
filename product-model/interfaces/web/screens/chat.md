---
entities:
  - entity: chat-message
    shows: [From, Text, Changes made, Error]
    collects: [Text]
  - entity: plan
    shows: [Opening]
  - entity: task
    shows: [Title]
  - entity: change
    shows: [What changed]
references:
  - kind: code
    role: implementation
    target: web/src/lib/components/ChatDock.svelte
  - kind: code
    role: implementation
    target: web/src/lib/chat.svelte.ts
---

# Chat

The chat dock beside Today and All tasks, and a collapsed tab during the rituals: today's conversation
with the assistant, opening with the plan's opening line, each reply's actions, and Undo on a
reply that changed something.
