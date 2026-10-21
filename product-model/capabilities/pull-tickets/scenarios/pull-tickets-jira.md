---
kind: primary
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User pulls Jira from the brain dump step
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Jira integration is on with its address, token and search saved
  kind: condition
  entities:
  - {entity: jira-integration, effect: reads, facts: ['On', Address, Personal access token, Search (JQL)]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: Jira runs the search and returns up to 50 tickets, assigned ones before unassigned
  kind: product
  actor: user
  entities:
  - {entity: jira-integration, effect: reads, facts: [Search (JQL)]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product leaves out each ticket whose key is already a ref on a Task, open, done or dropped, and each
    skipped one
  kind: product
  actor: user
  entities:
  - {entity: task, effect: reads, facts: [Refs]}
  - {entity: skipped-item, effect: reads, facts: [Key]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product lists the rest unticked, each titled with its key and linked to Jira, with × to skip
  kind: product
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Pull Jira tickets to pick from

## Trigger

In the morning, the person wants to pick today's work from their sprint.

## Outcome

An unticked pick list shows tickets not yet on the list, the person's own first.

## Edge cases

- When more matched than were returned, the list ends with "N more matched — narrow the search".
- A deleted task's ticket can be offered again.
