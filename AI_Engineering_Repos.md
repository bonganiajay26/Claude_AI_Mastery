# AI Engineering — The Job-Ready Repo Study Guide

A tight, opinionated list of open-source repositories for building **job-ready AI engineering skills**. Focused on three pillars:

1. **AI agent frameworks**
2. **Workflow automation for AI**
3. **LLM-based applications (RAG, evaluation, production tooling)**

Every repo is actively maintained (checked April 2026), widely used in production, and has a runnable quickstart. No papers, no research-only code, no abandonware.

---

## Tier 1 — Foundations (Weeks 1–2)

### 1. anthropics/anthropic-cookbook
- Link: https://github.com/anthropics/anthropic-cookbook
- What it does: Official Claude recipes — tool-use, RAG, classification, vision, prompt caching, extended thinking.
- Skill level: Beginner
- Real-world use cases: Any Claude-powered product; ticket classification, document Q&A, structured extraction.
- Quick start:
  ```
  git clone https://github.com/anthropics/anthropic-cookbook
  pip install anthropic
  export ANTHROPIC_API_KEY=sk-...
  jupyter lab skills/
  ```
- Skills gained: The Messages API, tool-use loops, streaming, evals, structured outputs with JSON schemas.

### 2. openai/openai-cookbook
- Link: https://github.com/openai/openai-cookbook
- What it does: Same idea as the Anthropic cookbook, but from OpenAI — useful patterns that port cleanly to Claude.
- Skill level: Beginner
- Real-world use cases: Cross-provider reference; learning canonical patterns like function calling, batched inference, evaluation.
- Quick start: clone, pick a notebook, adapt to Claude using `anthropic` instead of `openai`.
- Skills gained: Portable LLM-engineering patterns; avoids "I only know one API" trap.

### 3. run-llama/llama_index
- Link: https://github.com/run-llama/llama_index
- What it does: Data framework for LLM apps — ingestion, indexing, query engines, sub-question routing.
- Skill level: Beginner → Intermediate
- Real-world use cases: Enterprise doc chatbots, knowledge retrieval, multi-document QA.
- Quick start:
  ```
  pip install llama-index llama-index-llms-anthropic
  ```
  Follow the starter tutorial: load a folder of PDFs, build an index, ask questions.
- Skills gained: Document loaders, node parsing, retrievers, query engines, sub-question decomposition.

### 4. langchain-ai/langchain
- Link: https://github.com/langchain-ai/langchain
- What it does: The broadest LLM app framework — chains, memory, retrievers, tools, agents.
- Skill level: Beginner → Intermediate
- Real-world use cases: Chatbots, RAG pipelines, agents, provider-agnostic prototyping.
- Quick start:
  ```
  pip install langchain langchain-anthropic
  ```
- Skills gained: LCEL (LangChain Expression Language), composing chains, retrievers, streaming, tracing.

### 5. mlabonne/llm-course
- Link: https://github.com/mlabonne/llm-course
- What it does: Structured, hands-on LLM curriculum with runnable notebooks — from fundamentals to fine-tuning to deployment.
- Skill level: Beginner → Advanced
- Real-world use cases: Self-study; interview prep; building your own 30-day ramp.
- Quick start: clone; pick the "LLM Scientist" or "LLM Engineer" track; run notebooks in Colab.
- Skills gained: Tokenization, transformer intuition, fine-tuning, quantization, inference optimization — enough to speak fluently in interviews.

---

## Tier 2 — Agent frameworks (Weeks 3–5)

### 6. langchain-ai/langgraph
- Link: https://github.com/langchain-ai/langgraph
- What it does: Stateful agent orchestration as a directed graph — nodes, edges, checkpoints, human-in-the-loop.
- Skill level: Intermediate → Advanced
- Real-world use cases: Durable customer-support agents, approval workflows, long-running research tasks.
- Quick start:
  ```
  pip install langgraph langchain-anthropic
  ```
  Build the "ReAct agent" example; then add a `human_approval` interrupt node.
- Skills gained: State machines, checkpointing, interrupt-and-resume, tool routing, observable traces.

### 7. crewAIInc/crewAI
- Link: https://github.com/crewAIInc/crewAI
- What it does: Role-based multi-agent "crews" that cooperate on a task (researcher + writer + editor pattern).
- Skill level: Intermediate
- Real-world use cases: Content pipelines, research assistants, market-analysis bots.
- Quick start:
  ```
  pip install crewai crewai-tools
  ```
  Run the research-crew quickstart from the README.
- Skills gained: Task decomposition, agent roles, delegation, shared memory.

### 8. microsoft/autogen
- Link: https://github.com/microsoft/autogen
- What it does: Event-driven multi-agent framework (v0.4+ is fully async with a clean actor model).
- Skill level: Advanced
- Real-world use cases: Complex group-chat agents, nested workflows, simulation of team interactions.
- Quick start:
  ```
  pip install "autogen-agentchat" "autogen-ext[openai]"
  ```
  (swap the model client for an Anthropic adapter)
- Skills gained: Actor model, message routing, group chat patterns, rigorous agent testing.

### 9. pydantic/pydantic-ai
- Link: https://github.com/pydantic/pydantic-ai
- What it does: Type-safe agent framework built on Pydantic — structured outputs, tool schemas, dependency injection.
- Skill level: Intermediate
- Real-world use cases: Agents where correctness and types matter — finance, compliance, data extraction.
- Quick start:
  ```
  pip install pydantic-ai
  ```
- Skills gained: Schema-driven agent design, deterministic tool calling, testable AI code.

### 10. All-Hands-AI/OpenHands
- Link: https://github.com/All-Hands-AI/OpenHands
- What it does: An autonomous AI software engineer that reads issues, writes code, runs tests, and opens PRs.
- Skill level: Advanced (to study, not recreate)
- Real-world use cases: Inspiration for coding agents, sandboxed execution, benchmark evaluation.
- Quick start: follow the Docker quickstart; provide an LLM key.
- Skills gained: Sandboxing, tool design at scale, SWE-bench evaluation, browser+terminal integration.

---

## Tier 3 — Workflow automation for AI (Weeks 6–7)

### 11. n8n-io/n8n
- Link: https://github.com/n8n-io/n8n
- What it does: Self-hosted workflow automation with 400+ integrations and first-class AI nodes.
- Skill level: Intermediate
- Real-world use cases: Slack triage bots, form-to-CRM with Claude enrichment, daily digests.
- Quick start:
  ```
  docker run -it --rm -p 5678:5678 n8nio/n8n
  ```
- Skills gained: Triggers, webhooks, data transformation, credential management, error branches.

### 12. langflow-ai/langflow
- Link: https://github.com/langflow-ai/langflow
- What it does: Visual drag-and-drop builder for LangChain/LangGraph apps; exports to runnable Python.
- Skill level: Beginner → Intermediate
- Real-world use cases: Rapid prototyping of RAG pipelines, demos for non-technical stakeholders.
- Quick start:
  ```
  pip install langflow && langflow run
  ```
- Skills gained: Mental model of LLM pipelines; fast iteration; translating visual flows to code.

### 13. FlowiseAI/Flowise
- Link: https://github.com/FlowiseAI/Flowise
- What it does: Similar to Langflow but Node.js-based; strong focus on deployable agent APIs.
- Skill level: Intermediate
- Real-world use cases: SaaS prototypes, embedded chatbots with REST endpoints.
- Quick start:
  ```
  npx flowise start
  ```
- Skills gained: TS-based LLM tooling, API-first agent design, multi-tenant thinking.

### 14. activepieces/activepieces
- Link: https://github.com/activepieces/activepieces
- What it does: Open-source Zapier alternative, TypeScript-first, strong AI actions.
- Skill level: Intermediate
- Real-world use cases: Business-process automation with LLM steps (enrichment, classification, drafting).
- Quick start: Docker Compose from the repo.
- Skills gained: Workflow engines, reusable "pieces," TypeScript automation.

### 15. PrefectHQ/prefect
- Link: https://github.com/PrefectHQ/prefect
- What it does: Python-native orchestrator for data + AI pipelines (flows and tasks as decorators).
- Skill level: Intermediate
- Real-world use cases: Scheduled RAG ingestion, nightly evals, retraining pipelines.
- Quick start:
  ```
  pip install -U prefect
  prefect server start
  ```
- Skills gained: Orchestration, retries, deployments, observability for long-running AI jobs.

---

## Tier 4 — LLM apps & RAG (Weeks 8–9)

### 16. Mintplex-Labs/anything-llm
- Link: https://github.com/Mintplex-Labs/anything-llm
- What it does: Full-stack, multi-user RAG app with workspaces, connectors, and admin UI.
- Skill level: Intermediate → Advanced
- Real-world use cases: Internal company assistants; a strong reference architecture for RAG at scale.
- Quick start: Docker Compose one-liner from the README.
- Skills gained: Multi-tenant RAG, ACLs, embedding stores, UI patterns, config surfaces.

### 17. danswer-ai/onyx (formerly Danswer)
- Link: https://github.com/onyx-dot-app/onyx
- What it does: Open-source enterprise search + AI assistant connecting Slack, Drive, GitHub, Notion, etc.
- Skill level: Advanced
- Real-world use cases: Company-wide knowledge search, onboarding, customer-support copilots.
- Quick start: Docker Compose; follow the self-hosting guide.
- Skills gained: Connectors, ingestion pipelines, permissions, hybrid search, reranking.

### 18. assafelovic/gpt-researcher
- Link: https://github.com/assafelovic/gpt-researcher
- What it does: Autonomous research agent that writes report-quality documents with citations.
- Skill level: Intermediate
- Real-world use cases: Market research, competitive analysis, literature summaries.
- Quick start:
  ```
  pip install gpt-researcher
  ```
  then run a simple `researcher.run()`.
- Skills gained: Query decomposition, source ranking, multi-source synthesis.

### 19. browser-use/browser-use
- Link: https://github.com/browser-use/browser-use
- What it does: Connect any LLM to a real browser to perform tasks (form fill, scrape, book things).
- Skill level: Advanced
- Real-world use cases: QA automation, operations bots, end-to-end workflows that only exist behind logins.
- Quick start:
  ```
  pip install browser-use
  playwright install
  ```
- Skills gained: DOM observation → LLM action, safety rails, multimodal browser control.

### 20. unclecode/crawl4ai
- Link: https://github.com/unclecode/crawl4ai
- What it does: LLM-friendly web crawler producing clean, chunked, markdown-ready content for RAG.
- Skill level: Intermediate
- Real-world use cases: Building a custom knowledge base from public web sources.
- Quick start:
  ```
  pip install -U crawl4ai && crawl4ai-setup
  ```
- Skills gained: Smart extraction, metadata, RAG-ready preprocessing.

---

## Tier 5 — Production & evaluation (Week 10)

### 21. BerriAI/litellm
- Link: https://github.com/BerriAI/litellm
- What it does: Unified Python SDK and proxy server for 100+ LLM providers (OpenAI/Anthropic/Bedrock/Vertex).
- Skill level: Intermediate → Advanced
- Real-world use cases: Cost control, provider fallbacks, budget guards, multi-tenant routing.
- Quick start:
  ```
  pip install litellm
  litellm --model anthropic/claude-sonnet-4-6
  ```
- Skills gained: Gateway design, fallback routing, spend tracking, key management.

### 22. langfuse/langfuse
- Link: https://github.com/langfuse/langfuse
- What it does: Open-source LLM observability — tracing, prompt management, evals, analytics.
- Skill level: Intermediate → Advanced
- Real-world use cases: Production LLM apps; regression testing; cost/quality dashboards.
- Quick start: `docker compose up` from the repo; SDK integrates with LangChain, LangGraph, raw SDK.
- Skills gained: Tracing, prompt versioning, dataset-driven evaluation, online metrics.

### 23. stanfordnlp/dspy
- Link: https://github.com/stanfordnlp/dspy
- What it does: Programmatic prompt optimization — write signatures, let DSPy compile your prompts against metrics.
- Skill level: Advanced
- Real-world use cases: Any place hand-tuned prompts plateau — classification, extraction, agents.
- Quick start:
  ```
  pip install dspy-ai
  ```
- Skills gained: Declarative prompting, program-level optimization, teleprompter patterns.

### 24. explodinggradients/ragas
- Link: https://github.com/explodinggradients/ragas
- What it does: Evaluation framework for RAG — faithfulness, answer relevance, context precision.
- Skill level: Intermediate
- Real-world use cases: CI gates on RAG quality; comparing retrieval strategies.
- Quick start:
  ```
  pip install ragas
  ```
- Skills gained: LLM-as-judge evals, golden-dataset design, quality regression gates.

### 25. promptfoo/promptfoo
- Link: https://github.com/promptfoo/promptfoo
- What it does: Testing + eval framework for prompts and agents; YAML configs, red-teaming, CI.
- Skill level: Intermediate
- Real-world use cases: A/B prompt tests, safety red-teaming, CI integration for prompt changes.
- Quick start:
  ```
  npx promptfoo@latest init
  ```
- Skills gained: Treating prompts like code: versioned, tested, gated.

---

## The 10-week learning roadmap

| Week | Focus | Study | Ship |
|---|---|---|---|
| 1 | Foundations — Claude API & patterns | anthropic-cookbook + openai-cookbook | A Claude-powered classifier on 50 real inputs |
| 2 | RAG basics | llama_index starter + langchain | RAG over your own notes folder |
| 3 | Single-agent | langgraph ReAct template | 3-tool agent (search + DB + email) with tests |
| 4 | Multi-agent | crewAI + pydantic-ai | Research → writer → editor crew for a blog post |
| 5 | Advanced agents | autogen (study) + browser-use | Browser agent that does one real task daily |
| 6 | Visual workflows | langflow + n8n | n8n workflow with a Claude node saving you 1h/week |
| 7 | Orchestration | prefect | Nightly ingestion + eval + notification flow |
| 8 | Production RAG | anything-llm + onyx (study) | Multi-workspace RAG for your own projects |
| 9 | Research agents | gpt-researcher + crawl4ai | Weekly research digest agent |
| 10 | Quality & ops | litellm + langfuse + ragas + promptfoo + dspy | CI gate on a RAG pipeline using RAGAS + promptfoo |

---

## Portfolio-builder mode: three projects that get you hired

Pick exactly these three and build them well. They cover the spectrum interviewers test.

1. **Claude-powered RAG product**
   Stack: LangChain/LlamaIndex + pgvector + Claude + FastAPI + Next.js + Langfuse.
   Deliverable: public GitHub repo, 3-minute demo video, latency/cost/groundedness dashboard.
   Demonstrates: retrieval quality, citations, evals, deployment.

2. **Multi-agent automation**
   Stack: LangGraph (or CrewAI) + 3 tools (search, DB, email/Slack) + approval node + Langfuse tracing.
   Deliverable: agent that does a concrete job (e.g., support-ticket triage or lead enrichment) end-to-end.
   Demonstrates: state machines, tool design, safety, human-in-the-loop.

3. **LLM gateway + evaluation harness**
   Stack: LiteLLM proxy + promptfoo + RAGAS + DSPy (optional) + GitHub Actions.
   Deliverable: a reference repo showing prompt versioning, A/B routing, CI gates on quality.
   Demonstrates: production discipline — the thing most candidates lack.

---

## Principles while you study

- **Clone and run first, read second.** Running code makes reading code easier, not the other way around.
- **Write a `NOTES.md` per repo** with five things you learned and one thing you'd change.
- **Contribute once per tier** — docs, tests, or a tiny feature. Contribution in your commit history is worth more than a star on a todo app.
- **Pin versions.** AI APIs move fast; note the exact version of each repo you study so future-you can reproduce.
- **Measure everything.** If you can't put a number on the quality, cost, and latency of your AI system, you're guessing.

---

*Last updated: April 2026. All links verified on GitHub. If a repo has gone quiet for more than 6 months, replace it.*
