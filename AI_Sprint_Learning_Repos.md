# AI Sprint Learning — 15 Repos × 15 Mini Projects

A learn-by-shipping study plan for AI automation, agents, and LLM apps. Every repo here meets **three strict constraints**:

1. You can be productive in it within **1–3 days**.
2. It lets you build a **small, working project** quickly.
3. It is **actively maintained, widely used**, and **practical** (no research-only code, no heavy enterprise platforms).

Follow the day-by-day path. Each day = 1 repo + 1 shippable mini project. Commit every project to a public GitHub repo called `ai-sprint-<yourname>` to build a portfolio as you learn.

---

## Day 1 — Your first Claude app

### Repo 1: anthropics/anthropic-cookbook
- Link: https://github.com/anthropics/anthropic-cookbook
- What it does: Official Claude recipes (tool use, RAG, classification, vision, streaming).
- Why it fits a 1-day sprint: Every recipe is a single runnable notebook you can adapt in under an hour.
- Skill level: Beginner
- Mini project (4–6 hours): **"Inbox classifier"** — take 50 emails from a CSV, use the classification recipe to tag each as [billing, bug, sales, other] with JSON output and confidence scores. Produce an HTML report.
- Core skill: The Messages API, structured output, prompt design, basic evaluation.

### Repo 2: tiangolo/typer
- Link: https://github.com/fastapi/typer
- What it does: Turn Python functions into professional CLIs using type hints.
- Why it fits: You learn the entire framework in 2 hours; turns scripts into tools.
- Skill level: Beginner
- Mini project (2 hours): **Wrap Day 1's classifier in a CLI** — `inbox-ai classify emails.csv --model sonnet --out report.html`, with progress bar from `rich`.
- Core skill: CLI ergonomics; turning throwaway scripts into reusable tools.

---

## Day 2 — RAG in one sitting

### Repo 3: run-llama/llama_index
- Link: https://github.com/run-llama/llama_index
- What it does: Data framework for LLM apps — ingestion, indexing, querying.
- Why it fits: The 5-line starter tutorial gets you to a working RAG in 15 minutes.
- Skill level: Beginner → Intermediate
- Mini project (1 day): **"Notes chatbot"** — point LlamaIndex at a folder of your own notes (Obsidian, Notion export, or markdown), build an index, and chat with your knowledge base from the terminal.
- Core skill: Document loaders, indexing, query engines, citations.

### Repo 4: unclecode/crawl4ai
- Link: https://github.com/unclecode/crawl4ai
- What it does: Fetches web pages and emits clean, chunk-ready markdown for RAG.
- Why it fits: One command turns the public web into RAG-ready data.
- Skill level: Beginner → Intermediate
- Mini project (3 hours): **"Docs assistant"** — crawl your favorite framework's docs site, drop the markdown into Day 3's LlamaIndex, and build a terminal Q&A bot.
- Core skill: Smart web extraction, chunking, RAG pre-processing.

---

## Day 3 — Your first agent

### Repo 5: pydantic/pydantic-ai
- Link: https://github.com/pydantic/pydantic-ai
- What it does: Type-safe agents built on Pydantic with structured tool outputs.
- Why it fits: Cleanest mental model for tool calling; tiny learning curve.
- Skill level: Beginner → Intermediate
- Mini project (half day): **"Weather + news briefing agent"** — two tools (OpenWeather API, an RSS reader) and a Claude agent that emits a typed `Briefing` object every morning.
- Core skill: Tool schemas, type-safe agent outputs, deterministic testing.

### Repo 6: langchain-ai/langgraph
- Link: https://github.com/langchain-ai/langgraph
- What it does: Agents as stateful graphs with checkpoints and human-in-the-loop.
- Why it fits: The "create-react-agent" helper gets you a working agent in 10 lines.
- Skill level: Intermediate
- Mini project (1 day): **"Approval-gated booking agent"** — an agent with `search_flights` and `book_flight` tools; a human-approval node before booking. Persist state so it can resume.
- Core skill: State machines, interrupts, durable agents.

---

## Day 4 — Multi-agent crews

### Repo 7: crewAIInc/crewAI
- Link: https://github.com/crewAIInc/crewAI
- What it does: Role-based multi-agent "crews" that cooperate (researcher + writer + editor).
- Why it fits: Quickstart gives you a working 3-agent pipeline in under an hour.
- Skill level: Intermediate
- Mini project (1 day): **"Blog post crew"** — Researcher scrapes sources, Writer drafts, Editor polishes and fact-checks. Output: a 900-word post with citations.
- Core skill: Task decomposition, agent roles, delegation, shared memory.

---

## Day 5 — Visual workflow automation

### Repo 8: langflow-ai/langflow
- Link: https://github.com/langflow-ai/langflow
- What it does: Drag-and-drop builder for LangChain/LangGraph apps with Python export.
- Why it fits: You can build a non-trivial flow in an afternoon and export it to code.
- Skill level: Beginner → Intermediate
- Mini project (half day): **"PDF Q&A flow"** — upload a PDF, embed, retrieve, Claude answers with citations. Export the generated Python and run it as a standalone script.
- Core skill: Visual pipeline design; bridging prototype to production code.

### Repo 9: n8n-io/n8n
- Link: https://github.com/n8n-io/n8n
- What it does: Self-hosted Zapier alternative with a first-class AI node.
- Why it fits: Docker one-liner; build a production webhook workflow in an afternoon.
- Skill level: Intermediate
- Mini project (half day): **"Form-to-CRM enrichment"** — a public form triggers a flow that uses Claude to enrich the lead (company research, priority score), writes to Google Sheets, and pings Slack.
- Core skill: Triggers, webhooks, data transformation, LLM-in-the-loop automations.

---

## Day 6 — Browser and research agents

### Repo 10: browser-use/browser-use
- Link: https://github.com/browser-use/browser-use
- What it does: Connect an LLM to a real browser to do actual web tasks.
- Why it fits: Working browser agent in ~30 lines of Python.
- Skill level: Intermediate → Advanced
- Mini project (1 day): **"Job-listing collector"** — agent visits 3 job sites, filters for your criteria, and outputs a CSV of matches with URLs and a one-line summary each.
- Core skill: DOM observation → LLM action, safety rails, screenshots for audit.

### Repo 11: assafelovic/gpt-researcher
- Link: https://github.com/assafelovic/gpt-researcher
- What it does: Autonomous research agent that writes cited reports.
- Why it fits: `pip install`, one function call, full report out.
- Skill level: Intermediate
- Mini project (half day): **"Weekly market brief"** — schedule a nightly research run on a topic (e.g., "Claude developer ecosystem"). Email yourself a PDF every Monday.
- Core skill: Query decomposition, multi-source synthesis, citation hygiene.

---

## Day 7 — Polished UI + evaluation

### Repo 12: streamlit/streamlit
- Link: https://github.com/streamlit/streamlit
- What it does: Pure-Python framework for shippable LLM demos.
- Why it fits: Turn any agent into a shareable web app in under an hour.
- Skill level: Beginner
- Mini project (half day): **"Put Day 3's briefing agent on the web"** — a 60-line Streamlit app with a sidebar for preferences and a chat window. Deploy free to Streamlit Community Cloud.
- Core skill: Rapid UI for LLM apps; live demos for stakeholders.

### Repo 13: promptfoo/promptfoo
- Link: https://github.com/promptfoo/promptfoo
- What it does: Prompt testing & evaluation (YAML-defined, CI-ready).
- Why it fits: `npx promptfoo init` and a 2-file config is all you need.
- Skill level: Intermediate
- Mini project (2 hours): **"A/B your classifier"** — load the inbox classifier from Day 1 and run two prompt variants over 50 labeled rows; pick the winner by accuracy and cost.
- Core skill: Treating prompts as code — versioned, tested, gated.

---

## Day 8+ — Production discipline

### Repo 14: BerriAI/litellm
- Link: https://github.com/BerriAI/litellm
- What it does: Unified SDK + proxy for 100+ LLM providers with budgets and fallbacks.
- Why it fits: Proxy running in 5 minutes; add it to any earlier project to gain cost caps.
- Skill level: Intermediate
- Mini project (half day): **"Provider-agnostic brief generator"** — re-point any of your earlier scripts at the LiteLLM proxy. Add per-day budget limits and a fallback from Sonnet → Haiku on rate-limit errors.
- Core skill: Gateway thinking, fallback routing, cost observability.

### Repo 15: langfuse/langfuse
- Link: https://github.com/langfuse/langfuse
- What it does: Open-source LLM observability — traces, prompt versions, datasets, evals.
- Why it fits: `docker compose up` and a 2-line SDK init gets you full tracing.
- Skill level: Intermediate → Advanced
- Mini project (1 day): **"Trace your crew"** — instrument Day 4's CrewAI pipeline. Build a dataset of 10 topics, replay them nightly, and watch cost/latency/quality drift over time.
- Core skill: Observability, golden datasets, regression testing for AI.

---

## "What to do right now" — the first 60 minutes

1. **Minute 0–10:** create an empty public GitHub repo: `ai-sprint-<yourname>`. Add a `README.md` with the 15-project checklist from this guide.
2. **Minute 10–20:** sign up at console.anthropic.com; set `ANTHROPIC_API_KEY` in your shell profile; run one cookbook notebook to confirm it works.
3. **Minute 20–60:** start the Day 1 inbox classifier. You want a working first commit before you sleep.

---

## 8-day sprint schedule at a glance

| Day | Repo | Mini project | Core skill |
|---|---|---|---|
| 1 | anthropic-cookbook + typer | Inbox classifier CLI | Messages API, structured outputs |
| 2 | llama_index + crawl4ai | Notes/docs chatbot | RAG basics, web extraction |
| 3 | pydantic-ai + langgraph | Approval-gated agent | Tool use, state machines |
| 4 | crewAI | Blog-post crew | Multi-agent collaboration |
| 5 | langflow + n8n | PDF Q&A flow + form-to-CRM | Visual + production workflow |
| 6 | browser-use + gpt-researcher | Job collector + weekly brief | Browser + research agents |
| 7 | streamlit + promptfoo | Shareable UI + A/B test | UI + evaluation |
| 8+ | litellm + langfuse | Cost guard + observability | Production discipline |

---

## Principles for sprint learning

- **Ship daily.** A broken commit beats a perfect notebook you didn't push.
- **Write a 5-line `LEARNED.md`** in each mini-project: what worked, what broke, what you'd change.
- **Measure one metric** per project — accuracy, latency, cost, or time saved. "I shipped it" is not enough.
- **Stop when a repo doesn't fit the constraint.** If you're three days in and still configuring, pick a simpler repo and move on — the point is velocity.
- **Reuse earlier days.** Day 7's UI should wrap Day 3's agent; Day 8's observability should instrument Day 4's crew. Compounding is the whole game.

---

*Last updated: April 2026. Every repo verified active on GitHub within the last 30 days.*
