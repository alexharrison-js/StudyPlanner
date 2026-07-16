# ADR-003 AI Only When Intelligence Is Required

Status

Accepted

---

## Context

What problem is this solving?

AI is an expensive resource, and often introduces complexities that are unnecessary to the application.

---

## Decision

What architectural decision has been made?

LLMs should only be used where they provide genuine value.

Good AI tasks include:

- Summarizing research
- Extracting concepts
- Knowledge graph enrichment
- Curriculum generation
- Reflection analysis
- Quiz generation
- Topic novelty scoring

Business logic should remain deterministic whenever possible.

For example:

- Marking lessons complete
- Tracking streaks
- Scheduling reminders
- Recording ratings
- Updating timestamps

should never require an LLM.

---

## Rationale

Why was this approach selected?

There are plenty of wonderful software architecture and design patterns that accomplish almost all of what we need without involving AI. AI should only be used when information needs to be dynamically processed and applied.

Additionally, AI is expensive, so we want to limit usage.

---

## Alternatives Considered

Alternative 1 - Use AI for everything

Alternative 2 - Have an AI do decide when AI should be used (You can still do this (and you should!) as you're developing by consulting a chat llm - but the service shouldn't call AI first)

Alternative 3

---

## Consequences

Positive - Save money/tokens/compute. we are forced to confront the business logic and service logic during development and reflect on design more and that forces us to design more modular, decoupled, and efficient services.

Negative - some services are slower, some classes and services will need to be refactored over time if business logic proves suboptimal

Tradeoffs

---

## Related Principles

Links to other ADRs.
