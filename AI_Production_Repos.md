# AI Production Stack — 15 Repos Real Companies Actually Use

A curated list of open-source projects you'll find in real AI teams' `requirements.txt`, `package.json`, and job listings. Every repo below meets **four strict filters**:

1. **Actively maintained** (commits within the last 30 days as of April 2026).
2. **Used in production** at real companies — not hobby projects or research demos.
3. **Learnable in 1–3 days** for a focused learner.
4. **Industry-relevant** — the skills you gain match what AI Engineer / LLM Engineer / AI Architect job descriptions actually ask for.

Follow the three-part progression. Each repo has a concrete job-ready mini project. Commit everything to a public GitHub repo to build a portfolio as you go.

---

## Part 1 — Basic building blocks (Days 1–3)

These are the primitives. Almost every production AI system starts with them.

### 1. anthropics/anthropic-cookbook
- Link: https://github.com/anthropics/anthropic-cookbook
- What it does: Official Claude recipes — tool use, RAG, classification, vision, prompt caching.
- Used in production by: Anthropic customers shipping Claude features (thousands of companies reference these recipes).
- Skill level: Beginner
- 1–2 day project: **Ticket classifier** — take 100 real support tickets, classify into 6 categories with confidence scores and reasoning, output JSON; measure accuracy vs a hand-labeled test set.
- Job-relevant skill: Messages API, structured outputs, tool-use basics, simple evaluation — the foundation every interview assumes you know.

### 2. jxnl/instructor
- Link: https://github.com/jxnl/instructor
- What it does: Get Pydantic-validated structured output from any LLM, with automatic retries on schema failures.
- Used in production by: Shipped at numerous YC companies, Salesforce teams, data platforms — the standard for "LLM returns clean JSON."
- Skill level: Beginner
- 1 day project: **Invoice extractor** — feed 20 messy PDFs/images of invoices; return a validated `Invoice` pydantic model with vendor, line items, totals, and dates. Handle validation errors with retries.
- Job-relevant skill: Schema-driven LLM output — the single most-requested skill in 2026 LLM-engineer JDs.

### 3. BerriAI/litellm
- Link: https://github.com/BerriAI/litellm
- What it does: One unified SDK + proxy for 100+ LLM providers with budgets, fallbacks, caching, and logging.
- Used in production by: Netflix, Lemonade, Rocket Money, Adobe, Booking.com (per their own case studies).
- Skill level: Beginner → Intermediate
- 1–2 day project: **LLM gateway** — stand up the LiteLLM proxy with a $5/day budget, a Sonnet → Haiku fallback, and Redis-based response caching. Point two earlier scripts at it; measure cost reduction.
- Job-relevant skill: LLM gateway design, cost control, provider abstraction — the "platform" layer every serious AI team builds.

---

## Part 2 — The core stack (Days 4–9)

This is where you build the systems job descriptions actually ask for: RAG, agents, and evaluation.

### 4. run-llama/llama_index
- Link: https://github.com/run-llama/llama_index
- What it does: Data framework for LLM apps — ingestion, indexing, query engines, advanced retrieval.
- Used in production by: KPMG, Cemex, Carlyle, Traceloop (per LlamaIndex customer pages) and many more.
- Skill level: Intermediate
- 2 day project: **Policy Q&A bot** — ingest your company's handbook / public policies, build a hybrid retriever, answer questions with citations. Validate with a 20-question golden set.
- Job-relevant skill: Document ingestion, retrieval, citations — the RAG you'll ship in your first week on the job.

### 5. langchain-ai/langgraph
- Link: https://github.com/langchain-ai/langgraph
- What it does: Stateful agents as graphs — nodes, edges, checkpoints, interrupts for human-in-the-loop.
- Used in production by: Uber, Klarna, LinkedIn, Replit, Elastic (per LangChain's case studies), and is core to LangChain's enterprise offering.
- Skill level: Intermediate → Advanced
- 2–3 day project: **Approval-gated refund agent** — tools for `lookup_order`, `check_policy`, `issue_refund`; any refund > $100 hits a human-approval node that pauses execution and can be resumed.
- Job-relevant skill: Agent orchestration, durable state, human-in-the-loop — a direct match for production support and ops agents.

### 6. pgvector/pgvector
- Link: https://github.com/pgvector/pgvector
- What it does: Vector similarity search as a Postgres extension.
- Used in production by: Supabase, Neon, Timescale, Instacart, Notion (at minimum for experiments), thousands of startups via managed Postgres.
- Skill level: Intermediate
- 1 day project: **Hybrid search API** — Postgres table with 10k chunks of public docs; add a pgvector ivfflat index + tsvector full-text index; expose a FastAPI `/search` endpoint doing reciprocal-rank fusion.
- Job-relevant skill: Vector databases without vendor lock-in; hybrid retrieval — a top 2026 hiring signal.

### 7. crewAIInc/crewAI
- Link: https://github.com/crewAIInc/crewAI
- What it does: Multi-agent "crews" with roles, tasks, and delegation.
- Used in production by: Oracle NetSuite Analytics Warehouse team, Deloitte, PwC, AWS Accelerate partners (per public talks and case studies).
- Skill level: Intermediate
- 2 day project: **Content pipeline** — Researcher (search the web + summarize), Writer (drafts), Editor (fact-checks and polishes). Ships a 1000-word article with citations.
- Job-relevant skill: Multi-agent orchestration and delegation — increasingly common in enterprise AI JDs.

### 8. promptfoo/promptfoo
- Link: https://github.com/promptfoo/promptfoo
- What it does: Testing and evaluation for prompts and agents — YAML configs, CI integration, red-teaming.
- Used in production by: Discord, Shopify, Twilio, Meta, Google (per their public contributor logs and customer talks).
- Skill level: Intermediate
- 1 day project: **Prompt regression CI** — take your ticket classifier from Day 1; write a promptfoo config that runs 50 inputs across two prompt variants; wire it into GitHub Actions so every PR gets a quality report.
- Job-relevant skill: Prompts-as-code — treating LLM artifacts with the same discipline as application code.

---

## Part 3 — Production operations (Days 10–14)

Observability, workflow orchestration, and the glue that makes AI systems operable in the real world.

### 9. langfuse/langfuse
- Link: https://github.com/langfuse/langfuse
- What it does: Open-source LLM observability — traces, prompt management, datasets, online evals.
- Used in production by: Samsara, Khan Academy, Twilio, Merck, Springer Nature (per their customer page and OSS adopters).
- Skill level: Intermediate → Advanced
- 1–2 day project: **Trace your stack** — self-host Langfuse via Docker Compose; instrument your LangGraph refund agent and CrewAI content crew; build a dashboard showing cost, latency, and error rate per day.
- Job-relevant skill: LLM observability — the top capability separating "demo" engineers from "operator" engineers.

### 10. explodinggradients/ragas
- Link: https://github.com/explodinggradients/ragas
- What it does: RAG evaluation framework — faithfulness, answer relevance, context precision/recall.
- Used in production by: Appian, Intuit, Microsoft teams (per public talks and integrations), plus most RAG teams via Langfuse or Arize integrations.
- Skill level: Intermediate
- 1 day project: **RAG quality gate** — build a 30-question golden set for your Day 5 policy bot; run Ragas nightly with Prefect; fail the pipeline if faithfulness < 0.85.
- Job-relevant skill: LLM-as-judge evaluation + automated quality gates — asked about in every RAG-role interview.

### 11. deepset-ai/haystack
- Link: https://github.com/deepset-ai/haystack
- What it does: Modular RAG and agent framework built by deepset — pipelines, components, strong eval.
- Used in production by: NVIDIA, Airbus, Deutsche Telekom, Databricks customers (per deepset case studies).
- Skill level: Intermediate → Advanced
- 2 day project: **Hybrid RAG pipeline** — ingest 3 sources (Notion export, a PDF folder, a website via crawl4ai) into one Haystack pipeline with preprocessing, BM25 + embedding retrieval, reranker, and Claude generator.
- Job-relevant skill: Production RAG architecture from a framework explicitly designed for enterprise deployment.

### 12. n8n-io/n8n
- Link: https://github.com/n8n-io/n8n
- What it does: Self-hosted workflow automation with a first-class AI node (400+ integrations).
- Used in production by: Delivery Hero, NetApp, Sendcloud, thousands of SMBs and mid-market teams per n8n's published adopters.
- Skill level: Intermediate
- 1 day project: **Lead enrichment automation** — Typeform trigger → Claude enriches the lead (company research + priority score) → Google Sheets + Slack notification → HubSpot create contact. Real production shape.
- Job-relevant skill: Workflow automation with LLMs-in-the-loop — directly applicable to revenue ops, support, and internal tooling roles.

### 13. temporalio/sdk-python
- Link: https://github.com/temporalio/sdk-python
- What it does: Durable workflow orchestration used for long-running, retryable business processes.
- Used in production by: Stripe, Snap, Netflix, Coinbase, HashiCorp, Box, Datadog (per Temporal's public case studies).
- Skill level: Advanced
- 2 day project: **Durable research workflow** — a Temporal workflow that runs a gpt-researcher brief, stores results in pgvector, and emails a summary. Kill the worker halfway through; watch the workflow resume exactly where it left off.
- Job-relevant skill: Durable execution for AI — the pattern senior AI platform roles expect you to know.

### 14. browser-use/browser-use
- Link: https://github.com/browser-use/browser-use
- What it does: Connect an LLM to a real browser to perform concrete web tasks.
- Used in production by: Adoption growing fast at ops-automation teams; referenced in QA and growth-engineering playbooks in 2025–2026.
- Skill level: Intermediate → Advanced
- 2 day project: **Competitive-pricing monitor** — agent visits three competitor sites behind logins, extracts prices, logs to a Google Sheet, posts changes to Slack. Screenshots stored for audit.
- Job-relevant skill: Agentic browser automation — rapidly becoming a distinct specialty.

### 15. bentoml/BentoML
- Link: https://github.com/bentoml/BentoML
- What it does: Serve, package, and deploy ML/LLM models with production-grade APIs.
- Used in production by: Mission Lane, LINE, Bitcoin Depot, Naver, Yext (per BentoML adopters and case studies).
- Skill level: Intermediate → Advanced
- 1–2 day project: **Deployable Claude microservice** — wrap your Day 4 ticket classifier as a Bento service; build the container; deploy to a free tier; add request logging and health checks.
- Job-relevant skill: Packaging and deploying AI services — turns "runs on my laptop" into "runs on the cluster."

---

## "What to learn first, second, third" — the immediate roadmap

### First (Days 1–3): get one Claude feature shipping end-to-end.
- anthropic-cookbook → instructor → litellm.
- Outcome: a CLI tool that calls Claude, returns a validated Pydantic object, routes through a cost-guarded gateway.
- Why first: every later project assumes these three primitives.

### Second (Days 4–9): build the core RAG + agent stack.
- llama_index → pgvector → langgraph → crewAI → promptfoo.
- Outcome: two portfolio-grade systems — a cited policy Q&A bot, and a multi-agent content pipeline, both with A/B-tested prompts.
- Why second: these are the exact artifacts hiring managers ask to see in interviews.

### Third (Days 10–14): add the operator layer.
- langfuse → ragas → haystack → n8n → temporal → browser-use → bentoml.
- Outcome: the same systems from week 2, now with traces, quality gates, durable workflows, and a deployable API.
- Why third: this is the difference between a candidate who "built AI demos" and a candidate who can "ship AI systems." Most applicants never get here.

---

## The 14-day sprint schedule

| Day | Repo | Project | Part |
|---|---|---|---|
| 1 | anthropic-cookbook | Ticket classifier | 1 |
| 2 | instructor | Invoice extractor | 1 |
| 3 | litellm | Gateway + caching | 1 |
| 4 | llama_index | Policy Q&A bot | 2 |
| 5 | pgvector | Hybrid search API | 2 |
| 6–7 | langgraph | Approval-gated refund agent | 2 |
| 8 | crewAI | Content pipeline | 2 |
| 9 | promptfoo | Prompt regression CI | 2 |
| 10 | langfuse | Observability dashboards | 3 |
| 11 | ragas | RAG quality gate | 3 |
| 12 | haystack | Hybrid RAG pipeline | 3 |
| 13 | n8n + browser-use | Business automation + agent | 3 |
| 14 | temporal + bentoml | Durable workflow + deployed service | 3 |

---

## Principles so you actually ship

- **Pick one real problem you care about** and run it through every week. A generic "chatbot" learns you less than "refund-triage bot for my etsy store."
- **Commit daily, even broken.** The point is pace; refactor later.
- **Track one metric per project.** Accuracy, latency, cost, or hours saved. Recruiters remember numbers.
- **Write one `LEARNED.md` per repo** — five bullets, then move on. Perfect notes are procrastination.
- **Stop when a repo doesn't fit the filter.** If a repo needs three days just to configure, pick something simpler — the filter exists for a reason.

---

*Last updated: April 2026. Check each repo's GitHub activity graph before starting — if fewer than two commits in the last 60 days, swap it out.*
