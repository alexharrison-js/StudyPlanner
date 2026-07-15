Project Name:
StudyPanner

Project Vision:
StudyPanner is an asynchronous, provider-agnostic Personal Learning Operating System.

Unlike typical AI chat applications, StudyPanner treats LLMs as scarce background compute resources rather than synchronous dependencies.

The system is designed to maximize free-tier cloud resources, free-tier LLM quotas, and local inference while remaining fully functional without immediate AI availability.

Primary Goals

• Minimize synchronous LLM usage.
• Everything possible should be asynchronous.
• All AI work is represented as queued jobs.
• Workers process jobs whenever compute becomes available.
• Provider-agnostic architecture.
• Capability-based interfaces rather than provider-specific APIs.
• Modular microservices.
• Event-driven architecture.
• Local-first development.
• Production-quality software engineering.
• Dockerized.
• Open source.
• Anyone should be able to clone the repository, configure their own providers, and run the system using only free-tier accounts.

Architecture

Frontend
React
TypeScript
Vite

Backend
FastAPI

Storage
PostgreSQL
SQLite during development
Vector database
Knowledge graph

Core Services

API
Scheduler
Event Queue
Capability Router
Provider Registry
Compute Manager

Workers

Research
Summarization
Knowledge Extraction
Curriculum Planning
Reflection
Quiz Generation
Notifications

Provider Examples

Gemini
Hugging Face
OpenRouter
Ollama
Network-hosted Ollama
Future providers

Important Design Rules

• Never directly call a provider from business logic.
• Business logic requests capabilities.
• Capability Router chooses providers.
• Providers may fail.
• Jobs must be idempotent.
• Jobs may wait hours before processing.
• Cache all expensive operations.
• Gracefully degrade when no compute is available.
• Explain architectural tradeoffs before writing code.
• Prefer modular interfaces over concrete implementations.

Current Task

[Describe exactly one implementation task here.]

Deliverables

• Explain architecture.
• Explain design decisions.
• Implement production-quality code.
• Include tests where appropriate.
• Keep future scalability and provider abstraction in mind.
