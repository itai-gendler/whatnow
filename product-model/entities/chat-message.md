---
references:
  - kind: code
    role: implementation
    target: internal/domain/domain.go#Message
  - kind: code
    role: implementation
    target: internal/agent/agent.go
---

# Chat message

One message in the chat with the assistant: the person's, or the assistant's reply. Messages are kept
by date rather than by day, so chat works before the day is started, and each date starts a fresh chat.

## Information kept

- **Date** — the date it was sent
- **From** — the person or the assistant
- **Text** — what was said
- **Changes made** — each action the assistant took in the reply, with what it did or why it failed
- **Error** — set when the assistant couldn't reply; the text then says why in plain words
