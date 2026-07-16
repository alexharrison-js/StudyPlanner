# ADR-010 Configuration-Driven Architecture

Status

Accepted

---

## Context

What problem is this solving?

Things change. Providers are appear, or go out of business (well not really but we shouldn't rule it out). We get budget for compute, or we want to run a local llm instead of using a hosted one. Configuration files should handle all of these types of things (along with Environment variables for delicate information) and be easy to swap out for another option, without taking the system down.

---

## Decision

What architectural decision has been made?

The project should be configurable without code changes.

Configuration should define:

- Provider priority
- Preferred LLMs
- Retry policies
- Queue providers
- Storage providers
- Notification providers
- Scheduling intervals
- Cost limits

A user should be able to replace:

SQLite
↓
PostgreSQL
or
Gemini
↓
Local Ollama
without modifying application code.

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
