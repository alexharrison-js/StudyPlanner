# ADR-009 Resource-Aware Scheduling

Status

Accepted

---

## Context

What problem is this solving?

Accounting for Limited compute resources

---

## Decision

What architectural decision has been made?

Workers should never assume compute exists.

Every worker should ask:

- Is compute available?
- Is provider healthy?
- Does quota remain?
- Is a cheaper provider available?
- Has another worker already completed this task?

If not, return the task to the queue.

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
