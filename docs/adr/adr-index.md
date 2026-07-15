# Architecture Decision Record (ADR) Index

## Purpose

This document serves as the central index for all Architecture Decision Records (ADRs) within the StudyPlanner project.

StudyPlanner is designed as a long-lived, production-quality, open-source application. Significant architectural decisions are documented as ADRs so contributors can understand the reasoning behind the architecture, the alternatives considered, and the tradeoffs that were accepted.

The project manifesto can be found in:

- `docs/adr/Key_Principles.md`

That document defines the guiding philosophy of the project, while the ADRs below provide detailed justification and implementation guidance.

---

# ADR Status Definitions

| Status     | Meaning                         |
| ---------- | ------------------------------- |
| Proposed   | Under discussion                |
| Accepted   | Official project architecture   |
| Superseded | Replaced by another ADR         |
| Deprecated | Retained for historical context |

---

# Foundation ADRs

| ADR     | Title                                 | Status   |
| ------- | ------------------------------------- | -------- |
| ADR-001 | Free-Tier-First Architecture          | Accepted |
| ADR-002 | Asynchronous-by-Default Processing    | Accepted |
| ADR-003 | AI Only When Intelligence Is Required | Accepted |
| ADR-004 | Everything External Is a Provider     | Accepted |
| ADR-005 | Capability-Based Architecture         | Accepted |
| ADR-006 | Event-Driven Architecture             | Accepted |
| ADR-007 | Idempotent Background Processing      | Accepted |
| ADR-008 | Cache Expensive Operations            | Accepted |
| ADR-009 | Resource-Aware Scheduling             | Accepted |
| ADR-010 | Configuration-Driven Architecture     | Accepted |
| ADR-011 | Open Source First                     | Accepted |

---

# Future ADRs

Additional ADRs will be created as the project evolves.

Examples include:

- Worker lifecycle
- Resource Manager implementation
- Queue implementation
- Storage abstraction
- Knowledge graph architecture
- AI provider selection
- Testing strategy
- Observability
- Security
- Plugin architecture
