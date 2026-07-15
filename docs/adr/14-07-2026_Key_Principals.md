# Key Principles

## 1. Free Tier First

StudyPlanner is designed to operate using only free-tier infrastructure whenever possible.

The project assumes:

- Free cloud compute
- Free LLM quotas
- Local inference
- Self-hosted services

Paid services should simply increase throughput rather than change architecture.

Every feature should be designed with this philosophy in mind.

---

## 2. Asynchronous by Default

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

## 3. AI Only When Intelligence Is Required

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

## 4. Everything External Is A Provider

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

## 5. Capability-Based Architecture

Application code should request capabilities rather than implementations.

Example:

GenerateSummary()

rather than

CallGemini()

The Resource Manager is responsible for selecting the best available provider.

---

## 6. Event-Driven Architecture

Every significant action generates an event.

Examples:

- LessonCompleted
- QuizSubmitted
- UserFeedbackReceived
- ResearchCollected
- CurriculumUpdated
- NotificationSent

Workers subscribe to events and process them asynchronously.

---

## 7. Idempotent Processing

Every background task must be safe to execute multiple times.

Tasks should include:

- Unique IDs
- Retry count
- Status
- Completion timestamp
- Cache key

Workers should first determine whether work has already been completed before processing.

---

## 8. Cache Expensive Work

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

## 9. Resource-Aware Scheduling

Workers should never assume compute exists.

Every worker should ask:

- Is compute available?
- Is provider healthy?
- Does quota remain?
- Is a cheaper provider available?
- Has another worker already completed this task?

If not, return the task to the queue.

---

## 10. Configuration Controls Everything

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

## 11. Open Source First

StudyPlanner is designed to be cloned and self-hosted.

Users should be able to:

- Configure their own free-tier cloud accounts
- Use local models
- Connect to remote Ollama instances
- Replace providers through configuration

The architecture should encourage ownership rather than vendor lock-in.
