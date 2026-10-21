---
domain: integrations
references:
  - kind: code
    role: implementation
    target: internal/integrations/gcal/gcal.go#Calendar.Fields
  - kind: code
    role: implementation
    target: internal/integrations/runner.go#Runner.Save
---

# Calendar

One Google Calendar the person reads meetings from, such as Work or Personal, given by the calendar's
secret iCal address. One pull fetches every calendar.

## Information kept

- **Name** — the label its pulled meetings are grouped under
- **Secret address** — the calendar's secret address in iCal format, kept in the system keychain and shown only as saved
