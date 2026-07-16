# ADR-007 Idempotent Background Processing

Status

Accepted

---

## Context

What problem is this solving?

Because we have limited compute and llm resources, our application should be designed to cycle through available options based on the resource manager. Each provider should hold duplicates of jobs in job queues, and those may be called by any service/processor/worker at any time. We need to account for this.

---

## Decision

What architectural decision has been made?

Every background task must be safe to execute multiple times.

Tasks should include:

- Unique IDs
- Retry count
- Status
- Completion timestamp
- Cache key

Workers should first determine whether work has already been completed before processing.

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
