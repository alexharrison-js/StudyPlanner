# ADR-008 Cache Expensive Operations

Status

Accepted

---

## Context

What problem is this solving?

Limited resources mean reprocessing work is very expensive, so we need to limit duplicated processing wherever possible via caching.

---

## Decision

What architectural decision has been made?

Expensive AI operations should never be repeated unnecessarily.

Examples:

- Article summaries
- Concept extraction
- Quiz generation
- Embeddings
- Curriculum recommendations

Whenever possible:

Check Cache
↓
Exists?
↓
Return Cached Result
↓
Else Process

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
