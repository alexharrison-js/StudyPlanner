# ADR-002 Asynchronous-by-Default Processing

Status

Accepted

---

## Context

What problem is this solving?

Free tier accounts have significantly limited compute resources, and limited llm tokens. As a result of this, services and agents cannot freely run all the time without incurring cost.

---

## Decision

What architectural decision has been made?

AI is treated as a scarce compute resource.

No business workflow should depend on immediate LLM availability.

Instead of:

Service
→ LLM
→ Update Database

StudyPlanner prefers:

Service
→ Event Queue
→ Return Immediately
↓
Background Worker
↓
Resource Available?
↓
Process Task
↓
Persist Results
↓
Publish Completion Event

The application should remain responsive even if no AI providers are currently available.

---

## Rationale

Why was this approach selected?

The reasoning is that users likely interface with the application UI only a couple of times per day to catch up on articles, learn the next lessons in their chosen personal curriculum, or figure out the next exercizes to practice. Their feedback does not need to be immediately processed by an llm or even an application service, to get the intended affect on the overal study plan. It just needs to process feedback at some point, so we just run what we can when we can, and keep track.

---

## Alternatives Considered

Alternative 1 - Interfacing directly with llms for everything -> High cost tokens

Alternative 2 - Program business logic into services to process EVERYTHING and omit AI from the picture -> High compute cost.

Alternative 3 - Run a local LLM model and run the application locally on a user machine -> This should still be possible if the user has the available hardware to do so, and it can be configured into the application easily. Design of all services should account for this, and allow for non-managed messaging queues

---

## Consequences

Positive - low cost

Negative - delays and sometimes important feedback from user is not processed in time for the next lesson

Tradeoffs

---

## Related Principles

Links to other ADRs.

| ADR-003 | AI Only When Intelligence Is Required | Accepted |
