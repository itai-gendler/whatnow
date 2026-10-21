---
appliesTo:
- type: capability
  id: pull-tickets
- type: capability
  id: add-tickets
references:
- kind: code
  role: implementation
  target: internal/integrations/runner.go#onList.hides
- kind: code
  role: implementation
  target: internal/integrations/runner.go#Runner.listed
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-12-whatnow-jira-design.md
- kind: spec
  role: intent
  target: docs/superpowers/specs/2026-10-15-whatnow-review-queue-design.md
---

# A ticket on the list isn't offered again

A ticket whose key is the ref of an open task, or that is skipped, is never offered. One on a done or
dropped task isn't either, unless the source asks for it again, as Review Queue does when a review is
requested again. A deleted task doesn't count. Adding applies the same rule, so adding twice adds once.
