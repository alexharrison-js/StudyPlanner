# High Level

                    React Frontend
                          │
                   REST/WebSocket API
                          │

──────────────────────────────────────────
API Gateway
──────────────────────────────────────────
Event Bus / Message Queue
──────────────────────────────────────────
Research Workers
Summarization Workers
Knowledge Extraction Workers
Curriculum Workers
Reflection Workers
Quiz Workers
Notification Workers
──────────────────────────────────────────
Resource Manager
──────────────────────────────────────────
AI Providers
Storage Providers
Queue Providers
Vector Providers
Notification Providers
Scheduler Providers
──────────────────────────────────────────
Shared Storage Layer
Knowledge Graph
Vector Store
Research Documents
Curriculum
User Progress

# Architecture Philosophy

StudyPlanner is designed around one core assumption:

> External resources are unreliable.

Cloud compute may not be available.

LLM quotas may be exhausted.

Free-tier services may temporarily reject requests.

The application therefore assumes that every expensive operation is asynchronous and eventually consistent.

The user interface should remain responsive regardless of AI availability.

LLMs are treated as background workers rather than synchronous dependencies.

# Structure (first pass)

```text
studyplanner/

frontend/

backend/

services/

- api/
- scheduler/
- event_bus/
- resource_manager/
- provider_registry/
- cache/
- repositories/

workers/

- research/
- summarizer/
- extractor/
- curriculum/
- reflection/
- quiz/
- notifications/

providers/

- ai/
  - gemini/
  - ollama/
  - huggingface/
  - openrouter/
  - anthropic/

- storage/
  - sqlite/
  - postgres/
  - supabase/
  - neon/

- queue/
  - sqlite/
  - sqs/
  - pubsub/
  - redis/

- notifications/
  - discord/
  - email/
  - push/

- vector/
  - chroma/
  - pgvector/

- scheduler/
  - cron/
  - github_actions/
  - cloud_scheduler/

shared/

- events/
- contracts/
- interfaces/
- models/
- utils/

storage/

- relational/
- vector/
- graph/

docs/

- architecture/
- adr/
- diagrams/

infra/

- docker/
- terraform/
- deployment/
```
