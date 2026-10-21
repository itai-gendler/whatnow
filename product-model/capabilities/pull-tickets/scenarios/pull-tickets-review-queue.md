---
kind: alternate
routes:
  web: Web UI
  tui: Terminal UI
steps:
- text: The User pulls Review Queue
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: Review Queue returns its ranked queue, and the Product leaves out pull requests below the minimum score
  kind: product
  actor: user
  entities:
  - {entity: review-queue-integration, effect: reads, facts: [Address, Minimum score]}
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
- text: The Product leaves out each pull request already on an open Task, or on a done or dropped one unless its
    review was requested again
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
- text: 'The Product lists the rest unticked as "Review <id>: <title>", with "Score · reasons · estimate" as notes'
  kind: product
  entities: []
  contexts:
    web:
      place: web::good-morning
    tui:
      place: tui::good-morning
---

# Pull pull requests waiting on a review

## Trigger

The person runs Review Queue and wants today's reviews in whatnow.

## Outcome

The pick list shows pull requests in Review Queue's own order, each with its score, reasons and estimate.

## Edge cases

- whatnow never re-ranks; dismissals and penalties set in Review Queue apply.
- At most 50 are listed; the rest are counted.
