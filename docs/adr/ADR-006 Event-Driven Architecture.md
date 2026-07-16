# ADR-006 Event-Driven Architecture

Status

Accepted

---

## Context

What problem is this solving?

syncronous programming and limited compute resources

---

## Decision

What architectural decision has been made?

Every significant action generates an event.

Examples:

- LessonCompleted
- QuizSubmitted
- UserFeedbackReceived
- ResearchCollected
- CurriculumUpdated
- NotificationSent

Workers subscribe to events and process them asynchronously.

---

## Rationale

Why was this approach selected?

---

## Alternatives Considered

Alternative 1

Alternative 2

Alternative 3

---

## Consequences

Positive

Negative

Tradeoffs

---

## Related Principles

Links to other ADRs.
