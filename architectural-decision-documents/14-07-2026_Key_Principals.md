# Key Principals

## Free tier by default

- The assumption is that compute and llm resources and infrastructure is all living within free tier accounts so as to make this project accessible to anyone. While there may come a time where it is not viable if providers scale back their free tiers, at present I think it is possible
- It should be possible to swap out free tier accounts for paid accounts to scale this up for multiple users/full production scale numbers of users
- Design each service and feature with the above in mind

## No reliable resources, asyncronous by default

- AI and LLM and Agentic LLM access is a resource
- All services treat compute and llm resources as assumed busy resources. This means instead of:
  Service -> LLM -> Update data
  we always process in an asyncronous way like:
  Service -> Messaging Queue -> Chill
  (when compute resource is available) -> Service Lambdas run and parse messages in messaging queue -> Processed data goes to AI queue
  (when llm / agents are available) -> Agents take tasks from the AI queue, and process them when they are necessary

## AI is great but not always needed

- AI should be used for actual intellegence needed processing such as:
  - crawling for new articles/data for evolving topics (eg. AI Research papers or new frameworks)
  - summarizing articles and determining relevance scores
  - retraining other agents or reviewing one another's work
  - updating the use study curriculum based on user feeedback
- Whenever possible, use messaging queues, standard business logic based services to process data. You don't need an llm to parse user feedback about wether or not a lesson was useful or too difficult, unless there are user extensive feedback and descriptions in the response. Even in that case that feedback doesn't need to be processed immediately, just at some point between now and the next study session (or even later)

## Provider agnostic by default

- The goal is to make it possible to run for an individual on completely free-tier allocations of compute and llm tokens. To accomplish this:
  - All services (ideally lambdas) and listeners, routers etc are defined in Infrastructure as code in a way that can (ideally) be deployed to all cloud providers and spun up within the free tier.
  - Configuration files and environment variables take in user account details for all providers (paid or free accounts, or connection url and details for network or local running compute resources or llms for agents and chat where used)
  - Service behavior should default to asyncronous running, defaulting to punting tasks to message queues, tracking retries and completions, to allow for other services to pick them up if they fail or don't complete before resources (compute or ai) run out.
    - Example:
      - User reads a suggested article summary and full article on Agentic AI evaluation frameworks
      - User submits feedback from UI like "This article was not relevant, actually I want to read less academic articles and more hands on articles with demos"
      - Frontend submits to backend1 (backend services deployed in Azure)
      - Azure compute resources are down or unavailable due to free-tier limitations, and the call returns a 500
      - Frontend submits to backend2 (backend services deployed in AWS)
      - Aws backend resource processes and adds to the message queue, creating an ID hash for the task, and duplicating the task and tries to send it to all other message queues in other providers (Azure, GCP, OCI, etc).
      - AWS runs out of compute resources coincidentally right after that.
      - GCP has compute available in the account, and tries to call an openai agent, which fails due to no tokens. GCP tries to call a claude curriculum agent, which succeeds and takes the item from the GCP message queue
      - Claude curriculum agent fails or gets stalled as it runs out of tokens on the account.
      - GCP then tries to call a Gemini curriculum agent, which successfully processes the message queue, updates the curriculum for the user in the database, and updates article preferences in the database. After success, The message queue is updated and the hash is marked as completed.
      - GCP then tries to send out an update to other providers marking the message as completed
      - If another service gets resources and tries to run, it sees this task is completed and does not attempt.
  - There are challenges in this and it complicates things, but allows for a free process and when fully considered, can get as close to 'no repeated work' as possible.

## Configuration should determine preferences

- Config files should determine the order of preferences so that if the user prefers certain models or cloud providers those are tried first before others
