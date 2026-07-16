# ADR-004 Everything External Is a Provider

Status

Accepted

---

## Context

What problem is this solving?

All 3rd party resources (cloud computing, AI LLM interface, routers, storage, databases) are unreliable in that we can't control their availability. We don't want to be fully bound to anything external and as such it should all be designed as modular parts of a system.

---

## Decision

What architectural decision has been made?

StudyPlanner should never directly depend on a specific external implementation.

Every external dependency must be replaceable through configuration.

Provider categories include:

- AI Providers
- Storage Providers
- Queue Providers
- Notification Providers
- Scheduler Providers
- Vector Store Providers

Business logic should only depend on interfaces.

---

## Rationale

Why was this approach selected?

---

## Alternatives Considered

Alternative 1 - Build within one specific provider framework (AWS/Azure/GCP/OCI out of the box solutions). This is called vendor lockin, and while it can lead to an easier to understand mature system, this application is not necessarily designed for scale, but instead for budget and functionality.

Alternative 2 -

Alternative 3

---

## Consequences

Positive - We can cycle through additional cloud or llm providers as they appear to be available

Negative

Tradeoffs

---

## Related Principles

Links to other ADRs.
