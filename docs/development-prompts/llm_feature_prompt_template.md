# Project Context

## Project Name

StudyPlanner

---

## Project Vision

StudyPlanner is an asynchronous, provider-agnostic Personal Learning Operating System.

Unlike typical AI applications, StudyPlanner treats LLMs as scarce background compute resources rather than synchronous dependencies.

The system is designed to maximize free-tier cloud resources, free-tier LLM quotas, and local inference while remaining fully functional without immediate AI availability.

StudyPlanner's purpose is to continuously research topics, generate personalized learning plans, maintain long-term knowledge models, and adapt curricula while minimizing AI costs.

---

## Core Design Philosophy

- Free-tier first
- Asynchronous by default
- Event-driven architecture
- Provider-agnostic
- Resource-aware scheduling
- Cache expensive operations
- Interface-driven design
- Local-first development
- Open source
- Production-quality engineering

---

## Architecture

### Frontend

- React
- TypeScript
- Vite

### Backend

- FastAPI

### Storage

- SQLite (development)
- PostgreSQL (production)
- Vector Store
- Knowledge Graph

### Core Services

- API
- Scheduler
- Event Bus
- Resource Manager
- Provider Registry
- Cache Layer

### Workers

- Research
- Summarization
- Knowledge Extraction
- Curriculum Planning
- Reflection
- Quiz Generation
- Notifications

### Provider Categories

AI

- Gemini
- Ollama
- Hugging Face
- Anthropic
- OpenRouter

Storage

- SQLite
- PostgreSQL
- Supabase

Queues

- SQLite Queue
- AWS SQS
- Google Pub/Sub
- Redis

Notifications

- Discord
- Email
- Push

---

## Important Design Rules

- Never directly call provider implementations from business logic.
- Business logic requests capabilities.
- The Resource Manager selects providers.
- Every provider may fail.
- Workers must be idempotent.
- Jobs may remain queued for hours.
- Expensive AI work should be cached.
- Every external dependency should be replaceable through configuration.
- Explain architectural decisions before implementation.
- Prefer abstractions over concrete implementations.
- Keep services modular and independently deployable.

---

## Current Task

[Describe exactly one implementation task.]

---

## Deliverables

Please provide:

1. High-level architecture for this feature.
2. Design decisions and tradeoffs.
3. Recommended interfaces and abstractions.
4. Production-quality implementation.
5. Unit tests where appropriate.
6. Suggested project structure changes if needed.
7. Future extensibility considerations.
