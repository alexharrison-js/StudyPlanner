# High Level

                  React Frontend
                        │
                 REST/WebSocket API
                        │

──────────────────────────────────────────
Event Gateway
──────────────────────────────────────────
Central Event Queue
──────────────────────────────────────────
Research Workers
Summarization Workers
Reflection Workers
Planning Workers
Quiz Workers
Notification Workers
──────────────────────────────────────────
Capability Router
──────────────────────────────────────────
Gemini
Hugging Face
OpenRouter
Local Ollama
Network Ollama
Future Providers
──────────────────────────────────────────
Shared Database
Knowledge Graph
Vector Store
Research Documents
Curriculum
User Progress

# Structure (first pass)

```markdown
mentor-os/

frontend/

backend/

services/

- api/
- scheduler/
- queue/
- capability_router/
- provider_registry/
- compute_manager/

workers/

- research/
- summarizer/
- extractor/
- planner/
- reflection/
- quiz/
- notifications/

providers/

- gemini/
- ollama/
- huggingface/
- openrouter/
- mock/

shared/

- events/
- contracts/
- models/
- utils/

storage/

- postgres/
- vector/
- graph/

docs/

- architecture/
- adr/
- diagrams/

infra/

- docker/
- terraform/
```
