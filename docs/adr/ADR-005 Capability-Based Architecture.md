# ADR-005 Capability-Based Architecture

Status

Accepted

---

## Context

What problem is this solving?

Application code directly calling resources that are not available at present, and causing lag in the system or dead processes.

---

## Decision

What architectural decision has been made?

Application code should request capabilities rather than implementations.

Example:

GenerateSummary()

rather than

CallGemini()

The Resource Manager is responsible for selecting the best available provider.

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
