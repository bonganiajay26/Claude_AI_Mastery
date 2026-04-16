# 30-Day AI Automation Job-Readiness Plan

**Goal:** get interviews (and ideally offers) for AI Automation / LLM Engineer roles within 30 days.
**Assumed starting level:** intermediate — you can write Python, have used an API, and can read documentation.
**Daily time commitment:** 3–5 focused hours. Weekends are heavier build days.
**Non-negotiables:** public GitHub, a commit every day, a measurable output every day.

Create one public repository today named `ai-automation-portfolio-<yourname>`. Every day's output lives inside it under `day-01/`, `day-02/`, etc. By Day 30, the repo itself is your resume.

---

## Week 1 — Foundation (Days 1–7)

### Day 1 — Environment + first Claude calls
- **Learn:** Claude Messages API, auth, temperature, token budgets.
- **Build:** A 40-line Python script that summarizes a block of text with 3 different `temperature` values and logs input/output tokens.
- **Tools / repos:** [anthropics/anthropic-cookbook](https://github.com/anthropics/anthropic-cookbook), `uv` or `poetry`, `python-dotenv`.
- **Output:** `day-01/summarize.py` + screenshot of three outputs in the README.

### Day 2 — Structured output with Instructor
- **Learn:** Pydantic models, JSON schema coercion, retries on validation errors.
- **Build:** An invoice extractor that takes 10 messy invoice PDFs (use public samples) and returns a validated `Invoice` Pydantic model (vendor, line items, totals, due date).
- **Tools / repos:** [jxnl/instructor](https://github.com/jxnl/instructor), `pydantic`, `pypdf`.
- **Output:** `day-02/extract.py` + `results.csv` + a table in README showing accuracy on 10 samples.

### Day 3 — Polished CLIs
- **Learn:** Argument parsing, subcommands, progress bars, coloured output.
- **Build:** A single CLI `aitool` with `summarize` and `extract` subcommands that wraps Days 1–2.
- **Tools / repos:** [tiangolo/typer](https://github.com/fastapi/typer), [Textualize/rich](https://github.com/Textualize/rich).
- **Output:** `pipx install` works locally; asciinema or GIF in README.

### Day 4 — Python automation primitives
- **Learn:** `requests`, `BeautifulSoup`, rate limiting, scheduled jobs, parallel I/O with `httpx` + `asyncio`.
- **Build:** A scraper that pulls the top 50 HN posts, enriches each with Claude-generated 2-sentence summaries, and writes a Markdown digest file.
- **Tools / repos:** `httpx`, `beautifulsoup4`, `asyncio`, Claude.
- **Output:** `day-04/hn_digest.py` + a sample digest committed as `digest.md`.

### Day 5 — LLM gateway and cost control
- **Learn:** Provider abstraction, fallbacks, budget limits, response caching.
- **Build:** LiteLLM proxy running in Docker locally with a $5/day budget, Sonnet → Haiku fallback, Redis cache. Point Day 1–4 scripts at it.
- **Tools / repos:** [BerriAI/litellm](https://github.com/BerriAI/litellm), Redis, Docker.
- **Output:** `day-05/litellm-config.yaml` + a latency/cost comparison table (before/after caching).

### Day 6 — RAG fundamentals
- **Learn:** Chunking, embeddings, vector search, citations.
- **Build:** Chat-your-docs over a folder of your own notes / markdown files using LlamaIndex starter; always produce `[source]` citations.
- **Tools / repos:** [run-llama/llama_index](https://github.com/run-llama/llama_index), Chroma.
- **Output:** `day-06/notes_bot.py` + 5 sample Q&As in README showing correct citations.

### Day 7 — Week 1 mini project: Inbox Copilot CLI
- **Learn:** Composing the week into one tool.
- **Build:** A CLI that ingests an `mbox`/IMAP dump, classifies each email (billing/bug/sales/other), drafts a reply with Claude, and writes a report.
- **Tools / repos:** Instructor, LiteLLM, Typer, `imaplib`.
- **Output:** Demo video (2 min) + ASCII architecture diagram in README.

---

## Week 2 — Core automation skills (Days 8–14)

### Day 8 — Workflow automation 101
- **Learn:** Triggers, actions, credentials, branching, error handling.
- **Build:** In n8n (self-hosted via Docker), a workflow: form submission → Claude enriches lead → writes to Google Sheets → posts to Slack.
- **Tools / repos:** [n8n-io/n8n](https://github.com/n8n-io/n8n), a free Typeform, a Slack workspace.
- **Output:** Exported `.json` workflow in `day-08/` + screenshot of a real execution.

### Day 9 — n8n for business automations
- **Learn:** Multi-step flows, conditional branches, retries, webhooks.
- **Build:** "Daily brief" flow: scheduled trigger → crawl 3 RSS feeds → Claude composes a 5-bullet summary → emails you at 8 AM.
- **Tools / repos:** n8n, SMTP node, Claude node.
- **Output:** Screenshot of the first scheduled run landing in your inbox.

### Day 10 — Web scraping for AI pipelines
- **Learn:** JS-rendered pages, session handling, robots etiquette, chunk-ready markdown extraction.
- **Build:** Scraper that pulls a documentation site (e.g., FastAPI docs) and emits clean markdown ready for RAG.
- **Tools / repos:** [unclecode/crawl4ai](https://github.com/unclecode/crawl4ai), [microsoft/playwright-python](https://github.com/microsoft/playwright-python).
- **Output:** `day-10/corpus/` folder with 50+ cleaned markdown files.

### Day 11 — FastAPI service for AI
- **Learn:** REST design, async endpoints, Pydantic models, streaming responses.
- **Build:** A `/summarize` and `/extract` FastAPI service with streaming SSE output. Dockerize it.
- **Tools / repos:** `fastapi`, `uvicorn`, `sse-starlette`.
- **Output:** `curl` examples in README + Docker image builds cleanly.

### Day 12 — Vector DB with pgvector
- **Learn:** Postgres extensions, HNSW/IVFFlat indexing, hybrid search (vector + BM25) with reciprocal-rank fusion.
- **Build:** Load Day 10's corpus into pgvector; expose a FastAPI `/search` endpoint returning hybrid results.
- **Tools / repos:** [pgvector/pgvector](https://github.com/pgvector/pgvector), `psycopg`, `SQLAlchemy`.
- **Output:** Latency + recall numbers on a 10-question golden set.

### Day 13 — RAG evaluation
- **Learn:** Faithfulness, answer relevance, context precision; LLM-as-judge pitfalls.
- **Build:** Nightly eval script that runs a 20-question golden set against Day 12's RAG and fails if faithfulness < 0.85.
- **Tools / repos:** [explodinggradients/ragas](https://github.com/explodinggradients/ragas).
- **Output:** CI action (GitHub Actions) running the eval on PR; badge in README.

### Day 14 — Week 2 mini project: Docs Assistant API
- **Learn:** Putting RAG + API + eval together.
- **Build:** A deployable docs-assistant service for a framework you like. Streaming answers, citations, eval gate.
- **Tools / repos:** FastAPI + pgvector + LlamaIndex + Ragas + LiteLLM.
- **Output:** Deployed to Fly.io / Railway / Cloud Run free tier; public URL in README.

---

## Week 3 — AI agents + integrations (Days 15–21)

### Day 15 — Tool calling fundamentals
- **Learn:** JSON-schema tool definitions, tool-result loops, tool choice, safety.
- **Build:** A calculator + weather agent in raw SDK (no framework) that handles tool errors gracefully.
- **Tools / repos:** anthropic-cookbook "tool_use" notebooks.
- **Output:** `day-15/tool_loop.py` + 10 test cases.

### Day 16 — LangGraph stateful agents
- **Learn:** Graph nodes, state schemas, streaming, checkpoints.
- **Build:** A refund agent with `lookup_order`, `check_policy`, `issue_refund` tools.
- **Tools / repos:** [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph).
- **Output:** `day-16/refund_agent.py` + a Mermaid diagram of the graph in README.

### Day 17 — Human-in-the-loop
- **Learn:** Interrupts, approval gates, resuming from checkpoints.
- **Build:** Add an approval node to Day 16 — refunds > $100 require a human "yes" before execution. Simulate the approval via CLI input.
- **Tools / repos:** LangGraph `interrupt`.
- **Output:** Recording (GIF) showing a refund pausing for approval, then resuming.

### Day 18 — Multi-agent crews
- **Learn:** Role-based agents, task decomposition, delegation.
- **Build:** A content crew: Researcher → Writer → Editor produces a 1000-word article on a topic you pick, with citations.
- **Tools / repos:** [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI).
- **Output:** Two sample articles committed + a 1-paragraph critique of the crew's weaknesses.

### Day 19 — Browser agents
- **Learn:** DOM observation, action safety, artifact capture.
- **Build:** An agent that visits two competitor sites, scrapes prices, appends to a Google Sheet, and pings Slack on changes.
- **Tools / repos:** [browser-use/browser-use](https://github.com/browser-use/browser-use).
- **Output:** Logged screenshots + one successful end-to-end run recorded on video.

### Day 20 — Observability
- **Learn:** Traces, spans, prompt versioning, datasets, online evals.
- **Build:** Self-host Langfuse; instrument Day 16 refund agent and Day 18 crew; build a dashboard.
- **Tools / repos:** [langfuse/langfuse](https://github.com/langfuse/langfuse).
- **Output:** Screenshot of a trace and a cost-per-day chart in README.

### Day 21 — Week 3 mini project: Operations Agent
- **Learn:** Agent + tools + approval + observability, glued together.
- **Build:** A single "Ops Copilot" agent with 4 tools (search KB, create ticket, send Slack message, query DB), one approval gate, and Langfuse tracing.
- **Tools / repos:** LangGraph, Langfuse, Slack SDK.
- **Output:** 3-minute demo video + deployed endpoint.

---

## Week 4 — Portfolio + job prep (Days 22–30)

### Day 22 — Portfolio Project 1: polish
- **Learn:** Product thinking, README as a sales page, real eval numbers.
- **Build:** Promote Day 14's Docs Assistant API into **Portfolio Project 1** (see below). Add auth, rate limiting, logging, a short architecture doc.
- **Output:** Professional README with diagram, quickstart, metrics, demo link.

### Day 23 — Portfolio Project 2: polish
- **Learn:** Narrative ("what problem does this solve"), measurable outcomes.
- **Build:** Promote Day 21's Ops Copilot to **Portfolio Project 2**. Add 3 more tools, a small web UI (Streamlit), and deploy.
- **Output:** Public URL + README with "before/after" time saved numbers.

### Day 24 — Portfolio Project 3: Business automation
- **Learn:** Non-developer-friendly automations, ROI framing.
- **Build:** **Portfolio Project 3** — a 5-step n8n workflow that automates a real repetitive job you or someone you know does (e.g., inbound lead triage, competitor monitoring, customer onboarding). Must include a Claude step.
- **Output:** Exported `.json` + screenshot + 1-page case study (`case_study.md`).

### Day 25 — Deploy everything
- **Learn:** Free-tier deployment, HTTPS, environment management, secrets.
- **Build:** Push all three projects to a public deployment (Fly.io / Railway / Cloud Run). Standardize health checks and OpenAPI docs.
- **Output:** Three public URLs linked from main repo README.

### Day 26 — Resume + LinkedIn + GitHub presentation
- **Learn:** Resume bullets that recruiters skim for (numbers, tools, outcomes).
- **Build:** Update your resume using the template below. Rewrite your LinkedIn headline and about. Pin the three projects on GitHub.
- **Output:** PDF resume committed to `career/resume.pdf`; LinkedIn updated.

### Day 27 — Interview prep: technical
- **Learn:** Common LLM/agent interview questions, systems design for LLM apps.
- **Build:** Work through the interview question list below. Write 1-page answers for 10 of them.
- **Output:** `career/interview_prep.md` committed.

### Day 28 — Interview prep: systems design
- **Learn:** Whiteboard a RAG system, an agent system, and a multi-tenant LLM app.
- **Build:** Three one-page architecture designs with tradeoffs.
- **Output:** `career/system_designs/` with three Markdown docs and Mermaid diagrams.

### Day 29 — Mock interviews + fixes
- **Learn:** Interview tempo, answering the "what's a project you're proud of" question.
- **Build:** Do two mock interviews (friend, peer, or interviewing.io). Record. Fix the two weakest answers.
- **Output:** `career/mocks.md` with self-critique.

### Day 30 — Apply + ship
- **Learn:** Targeted applications beat spray-and-pray.
- **Build:** Apply to **20 well-matched roles** with a tailored one-paragraph email per application referencing one of your three projects. Schedule 3 outreach messages to hiring managers on LinkedIn.
- **Output:** `career/applications.csv` (company, role, link, date, status) committed.

---

## The three portfolio projects in detail

### Portfolio Project 1 — Production-Grade Docs Assistant
- **What it does:** Answers questions over a documentation corpus with citations, hybrid search, streaming responses, and automated quality gates.
- **Tech stack:** Claude · FastAPI · LlamaIndex · pgvector · LiteLLM gateway · Ragas evals · Langfuse traces · Docker · Fly.io.
- **Steps to build:** (1) Crawl docs with crawl4ai → (2) chunk + embed into pgvector → (3) hybrid retrieval + reranker → (4) Claude generation with citations → (5) Ragas eval on 30-question golden set → (6) Langfuse traces → (7) Dockerize + deploy.
- **How to deploy / demo:** Public URL on Fly.io; README shows 3 example queries with citations; embed a Langfuse dashboard screenshot; include CI badge showing eval status.

### Portfolio Project 2 — Ops Copilot Agent
- **What it does:** A human-in-the-loop agent that triages internal requests (IT tickets, refund requests, sales asks), uses 4+ tools, and requires approval for high-risk actions.
- **Tech stack:** Claude · LangGraph · FastAPI · Streamlit UI · Slack SDK · Langfuse · Postgres.
- **Steps to build:** (1) Define the 4 tools → (2) LangGraph agent with tool-use loop → (3) approval interrupt node → (4) Slack integration for approvals → (5) Langfuse tracing → (6) Streamlit demo UI → (7) deploy.
- **How to deploy / demo:** Public Streamlit app + Loom video showing a real approval flow; include metrics (resolutions per hour, approval rate, cost per conversation).

### Portfolio Project 3 — Business Workflow Automation
- **What it does:** An n8n workflow that automates a real repetitive business job with a Claude step — examples: inbound-lead triage, competitor-price monitor, onboarding-email personalizer.
- **Tech stack:** n8n (self-hosted) · Claude node · a real SaaS integration (HubSpot / Slack / Notion / Google Sheets) · webhook.
- **Steps to build:** (1) Pick a real repetitive job → (2) map as a flow on paper → (3) build in n8n → (4) add Claude LLM step → (5) test with real data → (6) write a 1-page case study with ROI numbers.
- **How to deploy / demo:** Exported `.json` workflow + 2-minute Loom showing a real end-to-end run + `case_study.md` with "saved N hours/week."

---

## Portfolio repo structure

```
ai-automation-portfolio-<name>/
├── README.md                  # one-pager, pinned projects, contact
├── project-1-docs-assistant/
│   ├── README.md              # problem, stack, demo link, metrics
│   ├── app/                   # code
│   ├── evals/                 # ragas configs + golden set
│   ├── infra/                 # Dockerfile, fly.toml
│   └── architecture.md        # with Mermaid diagram
├── project-2-ops-copilot/
│   ├── README.md
│   ├── app/
│   ├── ui/                    # streamlit
│   ├── traces/                # sample langfuse exports
│   └── architecture.md
├── project-3-business-automation/
│   ├── README.md
│   ├── workflow.json          # exported n8n flow
│   ├── case_study.md
│   └── screenshots/
├── day-01/ ... day-30/        # daily work in order
└── career/
    ├── resume.pdf
    ├── interview_prep.md
    ├── system_designs/
    └── applications.csv
```

---

## Resume bullets (edit with your real numbers)

- Built a production RAG assistant over 50k documents with hybrid pgvector + BM25 retrieval, reaching **0.89 Ragas faithfulness** and **&lt; 1.2s p50 latency**; deployed on Fly.io with CI-gated evaluation.
- Designed a human-in-the-loop operations agent with LangGraph (4 tools, approval interrupts), deployed behind a Streamlit UI, tracing through Langfuse; reduced mock ticket resolution time by **62%** in internal tests.
- Shipped an n8n automation that enriches inbound leads with Claude, writes to HubSpot and Slack, saving an estimated **6 hours/week** per sales rep.
- Implemented a multi-provider LLM gateway on **LiteLLM** with Sonnet→Haiku fallback and Redis caching, cutting cost per request by **41%** while keeping answer quality within 2%.
- Instrumented two LLM services with **Langfuse** traces, prompt versioning, and nightly Ragas evals, enabling PR-level regression gates on prompt and retrieval changes.
- Productionized prompts with **promptfoo** A/B tests in GitHub Actions, turning prompt changes into reviewable, test-gated PRs.

---

## Jobs to apply to

- **AI Engineer** (generalist) — LLM app building, integrations, production shipping.
- **LLM Engineer / Applied AI Engineer** — deeper focus on prompts, agents, evals.
- **AI Automation Engineer** — workflow-heavy (n8n / Zapier / Make) with Claude/LLM steps.
- **Forward Deployed Engineer (AI)** — customer-facing + building integrations.
- **Machine Learning Engineer (LLMs)** — more ML rigor; good if you add fine-tuning later.
- **Developer Advocate / DevRel (AI)** — if you enjoy writing and demos.
- **Solution Architect / AI Consultant** — if you can talk ROI; contract work available quickly.

Target companies: startups building on Claude (Anthropic ecosystem directory), platform teams at mid-sized SaaS (every mid-sized SaaS has an "AI team" now), consulting orgs (Deloitte, Accenture, Slalom, boutiques), and internal tools teams at F500s.

---

## Interview questions to practice (answer all 20)

1. Walk me through your Docs Assistant — how do you measure quality?
2. Why did you pick Claude Sonnet vs Haiku vs Opus for each step?
3. Explain tokenization and why token counts affect cost and latency.
4. What is RAG, and when does it fail? How do you detect failure automatically?
5. How do you chunk documents — fixed, semantic, recursive — and when does each win?
6. Compare vector-only retrieval, BM25, and hybrid (RRF). Tradeoffs?
7. How would you add citations to a RAG pipeline so users can trust answers?
8. Walk me through a tool-use loop. How do you handle tool errors and retries?
9. ReAct vs Plan-and-Execute vs Reflexion — when would you use each?
10. How do you prevent prompt injection in an agent that has write tools?
11. Why use LangGraph instead of hand-rolled loops? When would you NOT use it?
12. How would you design multi-tenancy for a shared LLM gateway?
13. What's prompt caching and when does it pay off?
14. How do you version prompts and roll back a bad prompt in production?
15. What metrics would you put on a dashboard for an LLM feature in production?
16. How would you run an A/B test on a prompt change safely?
17. How do you estimate cost for a new LLM feature before shipping?
18. What's the difference between faithfulness, answer relevance, and context precision?
19. How would you fine-tune vs retrieve vs prompt? Decision tree?
20. Tell me about a time an LLM system behaved unexpectedly. What did you do?

Write 1-page answers. Practice the top 5 out loud with a timer (2 minutes each).

---

## First-hour starting checklist

1. Create the `ai-automation-portfolio-<name>` public GitHub repo.
2. Paste this plan's structure as the `README.md` outline with empty checkboxes.
3. Create `day-01/` folder; get the anthropic-cookbook running locally.
4. Set up `ANTHROPIC_API_KEY` and confirm a round trip.
5. Push your first commit today, even if it's one file.

---

## Principles for the 30 days

- **Momentum beats polish.** A committed day beats a perfect day you didn't ship.
- **Numbers in every README.** Faithfulness, latency, cost, hours saved. "I built this" is weak; "I built this and it saved 6 hours/week at 41% lower cost" is strong.
- **Every project solves a real problem.** Invent a target user; write their pain in the README.
- **Show your work.** Loom videos and GIFs make your portfolio 10× more convincing than code alone.
- **Apply while you build.** Start sending 5 tailored applications per week from Day 14, not Day 30 — the loop of interviews teaches you faster than any tutorial.

---

*Follow this for 30 days and you will have: three deployed projects, a credible GitHub repo, a tuned resume, an answered interview question list, and at least 20 live applications. That combination gets interviews.*
