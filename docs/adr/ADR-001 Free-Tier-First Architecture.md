# ADR-001 Free-Tier-First Architecture

Status

Accepted

---

## Context

What problem is this solving?

AI centric and cloud hosted applications incur high compute and llm resource (tokens) costs.

---

## Decision

What architectural decision has been made?

The project assumes:

- Free cloud compute
- Free LLM quotas
- Local inference
- Self-hosted services

Paid services should simply increase throughput rather than change architecture.

Every feature should be designed with this philosophy in mind.

---

## Rationale

Why was this approach selected?

- This is intended to be an open source project to allow anyone willing to set it up with their accounts the ability to take advantage of it without spending money.

StudyPlanner is designed to operate using only free-tier infrastructure whenever possible.

---

## Alternatives Considered

Alternative 1 - run at full scale by default

---

## Consequences

Positive - Anyone can do it without spending money

Negative - It does not scale well to multiple users, as compute resources and llm tokens will very quickly reach quotas, and unless there are endless alternative hosts and llms configured, it will hinder the processing of data by services

Tradeoffs - If you want to run it at scale you can use real resources and/or run it on your own hardware so long as you register domains etc.

---

## Related Principles

Links to other ADRs.

ADR-009 | Resource-Aware Scheduling
ADR-010 | Configuration-Driven Architecture
ADR-011 | Open Source First
