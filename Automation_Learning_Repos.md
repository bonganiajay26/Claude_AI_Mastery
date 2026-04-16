# Automation & Productivity — The Repo Study Guide

A curated, opinionated list of open-source repositories for building **real-world** automation and productivity skills. Every repo here is actively maintained, widely used, and practical (no theory-only books).

> How to use this guide: follow the roadmap at the bottom. Clone one repo per week, run it locally, break it, fix it, then ship a small project inspired by it.

---

## Level 1 — Beginner: Python automation fundamentals

### 1. geekcomputers/Python
- Link: https://github.com/geekcomputers/Python
- What it does: A collection of 150+ small Python scripts — renaming files, sending email, PDF merging, scraping, screen recorders, calculators, etc.
- Skill level: Beginner
- Why it is useful: You learn by reading short, self-contained automation scripts. Perfect for "how do I do X in Python" reflexes.
- Quick setup:
  ```
  git clone https://github.com/geekcomputers/Python
  cd Python && python3 FileRename.py
  ```
- You will learn: file I/O, subprocess, os/shutil, sending email, basic scraping, regex patterns.

### 2. Py-Contributors/awesomeScripts
- Link: https://github.com/Py-Contributors/awesomeScripts
- What it does: Community-curated automation scripts organized by category (web, files, OS, media).
- Skill level: Beginner
- Why it is useful: Great for picking a real chore (screenshot-on-schedule, WiFi password dumper, youtube downloader) and studying the idiomatic Python solution.
- Quick setup: clone, `pip install -r requirements.txt`, run any script.
- You will learn: CLI argparse, requests, third-party libraries, packaging a script into a tool.

### 3. Textualize/rich
- Link: https://github.com/Textualize/rich
- What it does: Beautiful terminal output — colors, tables, progress bars, markdown, syntax highlighting.
- Skill level: Beginner
- Why it is useful: Turning scripts into "tools people will actually use" is 50% good UX; `rich` teaches you that discipline.
- Quick setup: `pip install rich`; try `python -m rich`.
- You will learn: building pleasant CLIs, logging patterns, progress indicators.

### 4. tiangolo/typer
- Link: https://github.com/fastapi/typer
- What it does: Build command-line tools from Python type hints.
- Skill level: Beginner → Intermediate
- Why it is useful: Almost every automation turns into a CLI eventually. Typer is the fastest way to ship one.
- Quick setup: `pip install "typer[all]"`, copy an example from the README.
- You will learn: CLI design, subcommands, arguments vs options, auto-generated help and shell completion.

---

## Level 2 — Intermediate: real workflows, scraping, browser automation

### 5. scrapy/Scrapy
- Link: https://github.com/scrapy/scrapy
- What it does: Production-grade web scraping framework (spiders, pipelines, middlewares, throttling).
- Skill level: Intermediate
- Why it is useful: Teaches you how real scraping teams scale — concurrency, retries, politeness, pipelines to databases.
- Quick setup: `pip install scrapy`; `scrapy startproject tutorial` and follow the official tutorial.
- You will learn: async I/O, HTML/CSS/XPath selectors, middlewares, rate-limiting, data pipelines.

### 6. microsoft/playwright-python
- Link: https://github.com/microsoft/playwright-python
- What it does: Headless browser automation (Chrome, Firefox, WebKit) with modern JS support.
- Skill level: Intermediate
- Why it is useful: The modern successor to Selenium. Use for end-to-end tests, scraping JS-heavy sites, or automating internal tools.
- Quick setup: `pip install playwright && playwright install`; then `python -m playwright codegen https://example.com`.
- You will learn: selectors, auto-wait, tracing, video/screenshot capture, test generation.

### 7. n8n-io/n8n
- Link: https://github.com/n8n-io/n8n
- What it does: Self-hosted workflow automation with 400+ integrations (the open-source answer to Zapier/Make).
- Skill level: Intermediate
- Why it is useful: You learn *thinking in workflows* — triggers, nodes, data transformations, error branches.
- Quick setup:
  ```
  docker run -it --rm -p 5678:5678 n8nio/n8n
  ```
  Open http://localhost:5678.
- You will learn: webhooks, schedulers, credentials management, branching/merging data, JSON transformation.

### 8. huginn/huginn
- Link: https://github.com/huginn/huginn
- What it does: Self-hosted system for building "agents" that monitor and act on the web (RSS → email, weather alerts, price tracking).
- Skill level: Intermediate
- Why it is useful: A mental bridge between workflow engines and true agents. Teaches event-driven thinking.
- Quick setup: `docker run -p 3000:3000 huginn/huginn`.
- You will learn: agent design, scheduling, event propagation, long-running tasks.

### 9. ansible/ansible
- Link: https://github.com/ansible/ansible
- What it does: Agentless IT and configuration automation via SSH — install software, configure servers, orchestrate releases.
- Skill level: Intermediate
- Why it is useful: The DevOps automation workhorse. Even at small scale, Ansible playbooks replace fragile shell scripts.
- Quick setup: `pip install ansible`; `ansible-playbook -i inventory site.yml`.
- You will learn: YAML playbooks, inventories, roles, idempotency, secrets vaulting.

### 10. apache/airflow
- Link: https://github.com/apache/airflow
- What it does: Programmatic batch-pipeline orchestration in Python (DAGs, scheduler, executors).
- Skill level: Intermediate → Advanced
- Why it is useful: Industry-standard for data and analytics automation. Learning Airflow changes how you model any recurring job.
- Quick setup: `pip install "apache-airflow==2.9.*"` or use the Docker Compose quickstart.
- You will learn: DAG design, task retries/backfills, XCom, operators, SLA monitoring.

### 11. PrefectHQ/prefect
- Link: https://github.com/PrefectHQ/prefect
- What it does: A modern Python-native orchestrator — flows and tasks as decorators, dynamic DAGs, cloud or self-hosted.
- Skill level: Intermediate
- Why it is useful: Easier onramp than Airflow; excellent for ETL + AI pipelines. Cleaner failure handling.
- Quick setup: `pip install -U prefect`; run `prefect server start`.
- You will learn: declarative flows, state handlers, deployments, scheduling, observability.

### 12. home-assistant/core
- Link: https://github.com/home-assistant/core
- What it does: Open-source home automation platform with thousands of integrations.
- Skill level: Intermediate
- Why it is useful: If you have smart devices, this is a huge, well-architected async Python codebase to read and extend.
- Quick setup: follow https://www.home-assistant.io/installation/ (HAOS or container).
- You will learn: async Python, event buses, plugin architecture, state machines.

---

## Level 3 — Advanced: AI agents & LLM-powered automation

### 13. anthropics/anthropic-cookbook
- Link: https://github.com/anthropics/anthropic-cookbook
- What it does: Official Claude recipes — tool-use, RAG, evaluations, structured outputs, classifiers.
- Skill level: Intermediate → Advanced
- Why it is useful: The highest-signal starting point for Claude-powered automation. Every recipe is runnable.
- Quick setup: clone; set `ANTHROPIC_API_KEY`; `pip install -r requirements.txt` in the notebook folder.
- You will learn: message/tool API, streaming, RAG, prompt caching, vision, evaluation harnesses.

### 14. langchain-ai/langchain
- Link: https://github.com/langchain-ai/langchain
- What it does: Framework for building LLM applications — chains, retrievers, agents, memory, integrations.
- Skill level: Advanced
- Why it is useful: De facto ecosystem for LLM plumbing. Even if you don't use it in prod, reading it teaches the design patterns.
- Quick setup: `pip install langchain langchain-anthropic`.
- You will learn: LCEL, retrieval-augmented generation, tool-calling agents, streaming, tracing.

### 15. langchain-ai/langgraph
- Link: https://github.com/langchain-ai/langgraph
- What it does: Stateful agent orchestration as a graph (nodes, edges, checkpoints, human-in-the-loop).
- Skill level: Advanced
- Why it is useful: Production-ready agent pattern. Cleaner than ReAct loops; built for durability.
- Quick setup: `pip install langgraph langchain-anthropic`.
- You will learn: state machines for agents, checkpointing, interrupt-and-resume, approval gates.

### 16. crewAIInc/crewAI
- Link: https://github.com/crewAIInc/crewAI
- What it does: Multi-agent "crew" abstraction — role-based agents cooperating on a task.
- Skill level: Advanced
- Why it is useful: A very approachable way to learn multi-agent patterns and delegation.
- Quick setup: `pip install crewai`; copy the research crew quickstart.
- You will learn: agent roles, task decomposition, delegation, shared memory.

### 17. microsoft/autogen
- Link: https://github.com/microsoft/autogen
- What it does: Research-grade multi-agent framework (AutoGen v0.4 is async, event-driven).
- Skill level: Advanced
- Why it is useful: Teaches rigorous multi-agent design — message passing, group chat, nested agents.
- Quick setup: `pip install -U "autogen-agentchat" "autogen-ext[openai]"` (Claude via adapter).
- You will learn: actor model, group chat patterns, tool use at scale.

### 18. All-Hands-AI/OpenHands
- Link: https://github.com/All-Hands-AI/OpenHands
- What it does: An autonomous AI software engineer — reads tickets, writes code, runs tests, opens PRs.
- Skill level: Advanced
- Why it is useful: One of the most serious open-source attempts at a coding agent. Excellent reference for sandboxing and tool design.
- Quick setup: run via Docker per the README; provide an LLM key.
- You will learn: sandboxed execution, browser+terminal tools, evaluation on SWE-bench.

### 19. browser-use/browser-use
- Link: https://github.com/browser-use/browser-use
- What it does: Connect any LLM to a real browser to perform tasks (fill forms, scrape, book things).
- Skill level: Advanced
- Why it is useful: The modern pattern for web automation + LLMs; clean, minimal core.
- Quick setup: `pip install browser-use` + `playwright install`; set an LLM key.
- You will learn: DOM observation → LLM action, safety rails, multimodal browser control.

### 20. unclecode/crawl4ai
- Link: https://github.com/unclecode/crawl4ai
- What it does: LLM-friendly web crawler — produces clean, chunked, markdown-ready content for RAG.
- Skill level: Intermediate → Advanced
- Why it is useful: Bridges scraping and AI. Teaches you how to prepare the web for an LLM pipeline.
- Quick setup: `pip install -U crawl4ai` then `crawl4ai-setup`.
- You will learn: smart extraction, chunking, metadata, RAG-ready output.

---

## Level 4 — Career-grade polish: testing, quality, and shipping

### 21. robotframework/robotframework
- Link: https://github.com/robotframework/robotframework
- What it does: Generic keyword-driven automation/test framework. Used heavily in RPA and QA.
- Skill level: Intermediate
- Why it is useful: Industry-standard for non-developer-friendly automation (test engineers, QA, RPA).
- Quick setup: `pip install robotframework`; write a `.robot` file.
- You will learn: keyword-driven design, test suites, libraries, reports.

### 22. pyscaffold/pyscaffold
- Link: https://github.com/pyscaffold/pyscaffold
- What it does: Generates best-practice Python project skeletons (tests, CI, packaging, docs).
- Skill level: Beginner → Intermediate
- Why it is useful: Turns scripts into real packages. A non-negotiable professional habit.
- Quick setup: `pipx install pyscaffold`; `putup my-tool`.
- You will learn: packaging, entry points, tox, CI templates.

### 23. pre-commit/pre-commit
- Link: https://github.com/pre-commit/pre-commit
- What it does: Hooks that auto-format and lint every commit.
- Skill level: Beginner
- Why it is useful: The smallest, highest-leverage automation you can add to your own workflow.
- Quick setup: `pipx install pre-commit`; `pre-commit install`.
- You will learn: git hooks, linting pipelines, reproducible tooling.

---

## A 12-week learning roadmap

| Weeks | Focus | Repos to study | Deliverable |
|---|---|---|---|
| 1 | Script reflexes | geekcomputers/Python, Py-Contributors/awesomeScripts | Rewrite 3 scripts as your own CLI |
| 2 | Pleasant CLIs | Textualize/rich, tiangolo/typer | Ship a CLI to PyPI |
| 3 | Quality habits | pre-commit, pyscaffold | Convert week-2 tool to a real package |
| 4 | Browser automation | playwright-python | Automate one real site login + export |
| 5 | Scraping at scale | Scrapy, crawl4ai | Build a crawler with pipelines |
| 6 | Workflow thinking | n8n | Build a 3-step workflow (webhook → transform → Slack) |
| 7 | IT automation | ansible | Provision a VM from scratch |
| 8 | Pipeline orchestration | prefect or airflow | A daily ETL with retries and alerting |
| 9 | LLM plumbing | anthropic-cookbook, langchain | Ship a Claude-powered classifier or summarizer |
| 10 | Agent patterns | langgraph, crewAI | A 3-tool Claude agent with approval gate |
| 11 | Browser + LLM | browser-use | An agent that does a real task in your browser |
| 12 | Portfolio polish | all of the above | 3 public repos with READMEs, CI, demos |

### Why this order
- Scripts → CLIs → packages teaches craft before ambition.
- Browser and scraping come before workflow engines because they give you *things to orchestrate*.
- Workflow engines (n8n, Airflow, Prefect) before AI agents because modern agents are workflow engines with an LLM node — learn the substrate first.
- LangGraph/CrewAI last because multi-agent complexity without workflow instincts is how projects become unmaintainable.

### Principles while you study
- Clone, **run it**, then read the code. Running first makes the code make sense.
- For every repo, write a `NOTES.md` with 5 things you learned and 1 thing you'd change.
- Pick one repo per level to contribute to — a doc fix, a test, or a tiny feature. Shipping > lurking.
- Keep a "lessons" repo of your own with 1 small automation per week.

---

*Last updated: April 2026. Pin a version of each repo you study — APIs move fast.*
