<div align="center">
  <img src="https://nemilia.com/screenshots/full_logo.png" alt="Nemilia AI Workspace" width="340" />

  <h1>Nemilia — AI Workspace v2.0</h1>

  <p><strong>Your entire AI team. One file. Any provider.</strong></p>

  <p>
    Multi-agent orchestration &nbsp;·&nbsp; Document RAG &nbsp;·&nbsp; Live web research &nbsp;·&nbsp; Offline WebLLM<br/>
    Custom API providers &nbsp;·&nbsp; Zero servers &nbsp;·&nbsp; Zero installs &nbsp;·&nbsp; 100% client-side
  </p>

  <p>
    <a href="https://nemilia.com">nemilia.com</a> &nbsp;·&nbsp;
    <a href="mailto:luis@nemilia.com">luis@nemilia.com</a>
  </p>

  <img src="https://img.shields.io/badge/version-2.0-gold" alt="version" />
  <img src="https://img.shields.io/badge/license-BSL_1.1-orange" alt="license" />
  <img src="https://img.shields.io/badge/backend-none-brightgreen" alt="no backend" />
  <img src="https://img.shields.io/badge/install-open%20HTML%20file-brightgreen" alt="install" />

</div>

---

**A browser-native AI workspace with multi-agent orchestration, human-in-the-loop review, semantic vector RAG, reasoning model support, visual workflow design, and real-time cost tracking — all in a single HTML file with zero backend.**

*Nemilia (neh-mee-lee-ah) — Nahuatl for "to think, to remember, to imagine"*

---

## Table of Contents

- [What Is Nemilia?](#what-is-nemilia)
- [Why It Exists](#why-it-exists)
- [Screenshots](#screenshots)
- [Three Ways to Run](#three-ways-to-run)
- [Core Concepts](#core-concepts)
- [Feature Overview](#feature-overview)
  - [Chat Mode](#chat-mode)
  - [Compose & Workflow Mode](#compose--workflow-mode)
  - [Auto Workflow (AI Agent Routing)](#auto-workflow-ai-agent-routing)
  - [Agents & Orchestration](#agents--orchestration)
  - [Human-in-the-Loop (HITL)](#human-in-the-loop)
  - [Workflow Builder](#workflow-builder)
  - [Document RAG](#document-rag)
  - [Web Search](#web-search)
  - [Image & Visual Generation](#image--visual-generation)
  - [Browser-Native AI (WebLLM)](#browser-native-ai-webllm)
  - [Workspace & Storage](#workspace--storage)
  - [Memory System](#memory-system)
  - [Templates & Output](#templates--output)
  - [MCP Tool Execution](#mcp-model-context-protocol--tool-execution)
- [MCP (Model Context Protocol)](#mcp-model-context-protocol--tool-execution)
- [Architecture](#architecture)
- [Security & Privacy](#security--privacy)
- [Provider Reference](#provider-reference)
- [Quick Start](#quick-start)
- **Tutorials**
  - [Connecting an AI Provider](#tutorial-connecting-an-ai-provider)
  - [Your First Workflow Run](#tutorial-your-first-workflow-run)
  - [Creating Custom Agents](#tutorial-creating-custom-agents)
  - [Building Workflows with Drag-and-Drop](#tutorial-building-workflows-with-drag-and-drop)
  - [Human-in-the-Loop (HITL) Review](#tutorial-human-in-the-loop-hitl-review)
  - [Document RAG (Upload & Search)](#tutorial-document-rag-upload--search)
  - [Web Search with NEXUS](#tutorial-web-search-with-nexus)
  - [Using Web Search in Chat](#tutorial-using-web-search-in-chat)
  - [Image Generation with VISION](#tutorial-image-generation-with-vision)
  - [Running Local Models (WebLLM)](#tutorial-running-local-models-webllm)
  - [Connecting a Custom API Provider](#tutorial-connecting-a-custom-api-provider)
  - [Workspace & File Management](#tutorial-workspace--file-management)
  - [Prompt Templates](#tutorial-prompt-templates)
  - [Memory System](#tutorial-memory-system)
  - [Per-Agent Temperature](#tutorial-per-agent-temperature)
  - [MCP Tool Execution](#tutorial-mcp-tool-execution)
- [Settings Reference](#settings-reference)
- [Execution Flow](#execution-flow)
- [Browser Compatibility](#browser-compatibility)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Changelog](#changelog)
- [License](#license)

---

## What Is Nemilia?

Nemilia AI is an entirely client-side AI platform packed into a single, self-contained HTML file. There is no server, no installer, no account to create, and no database to configure. You open one file in a browser and get a full multi-agent AI workspace.

At its core, Nemilia lets you define **specialist AI agents** — each with a distinct role, personality, system prompt, and temperature — then wire them into **pipelines called workflows**. When you run a workflow, Nemilia orchestrates the agents in dependency order: a research agent gathers information, an analyst extracts insights, a writer produces content, a reviewer critiques it, and a synthesizer merges everything into a polished final report. Each agent's output is scored for quality and automatically retried if it falls short.

This is not a chatbot. It is a structured AI workspace where multiple models collaborate on complex tasks with human oversight at every stage. (Though it does have a great chat mode too.)

### What Can You Do With It?

- **Chat** — persistent multi-turn conversations with streaming, document context, memory injection, and live web search. Conversations auto-title and persist across sessions.
- **Research reports** — SCOUT researches a topic, LENS analyses findings, QUILL writes the report, FORGE reviews it, WEAVE synthesizes everything into an executive summary. Five agents, one click.
- **Auto workflows** — describe your task and the AI orchestrator selects the right agents, orders them logically, and runs the pipeline automatically. No manual workflow setup needed.
- **Document Q&A** — upload a 200-page PDF, ask questions, and get answers grounded in specific passages with hybrid semantic + keyword search.
- **Live web research** — NEXUS searches the internet in real-time, then downstream agents process and synthesize the results with source citations.
- **Visual content** — VISION generates Chart.js charts, SVG diagrams, HTML infographics, and (optionally) AI-generated images from DALL·E, FLUX, Stable Diffusion, and more.
- **Offline AI** — run Llama, Phi, Qwen, or Gemma directly in your browser via WebLLM. No API key, no server, no internet after the initial model download.
- **Review and steer** — pause the pipeline at any agent with human-in-the-loop checkpoints. Approve the output, edit it inline, or send feedback to re-run that step.
- **Track costs in real time** — live token count and estimated dollar cost update as every agent streams, so you always know what a run costs before it finishes.

### What Makes This Different?

| Feature | Nemilia | Typical AI Chat | AI Platform (Langchain, etc.) |
|---------|---------|-----------------|-------------------------------|
| Setup | Open an HTML file | Create account | Install Python, Docker, etc. |
| Chat | Persistent with RAG + memory + web search | Basic chat | Requires custom code |
| Multi-agent | Built-in orchestrator + auto-routing | Single model | Requires custom code |
| Human review | One-click HITL with audio alert | None | Custom implementation |
| Data privacy | 100% client-side | Data on their servers | Varies |
| Document search | Hybrid vector + BM25 | Upload & hope | Vector DB setup |
| Provider lock-in | Any provider, swap anytime | Locked to one | Configurable but complex |
| Offline mode | WebLLM in-browser | No | No |
| Cost tracking | Real-time per-token est. cost | Post-hoc (maybe) | Custom logging |
| Agent tuning | Per-agent temperature + model override | N/A | Code-level |

---

## Why It Exists

Most AI tools require you to trust a platform with your data, pay for a subscription, and accept whatever interface they provide. Nemilia takes a different approach:

- **Zero infrastructure** — no Docker, no Python environment, no `npm install`. One HTML file, any browser.
- **You own the runtime** — the code is open, readable, and runs on your machine. Nothing is obfuscated or phoned home.
- **Provider-agnostic** — switch between OpenAI, Anthropic, Groq, a local Ollama server, or in-browser WebLLM with a dropdown change. Your workflows don't lock you in.
- **Offline-capable** — with WebLLM and cached documents, Nemilia works without internet after initial setup.
- **Workspace portability** — sync to a local folder and your agents, prompts, and workflows become plain JSON and Markdown files you can version-control, share, or edit in any text editor.
- **Transparent costs** — real-time token and dollar estimates for every run, every agent, no surprises on your API bill.

---

## Screenshots

### Workspace

<div align="center">
  <img src="https://nemilia.com/screenshots/workspace.png" alt="Nemilia workspace folder setup" width="49%" />
  <img src="https://nemilia.com/screenshots/main.png" alt="Nemilia compose interface" width="49%" />
</div>

---

### Workflow Builder & Pipeline Modes

<div align="center">
  <img src="https://nemilia.com/screenshots/Workflow_edit.png" alt="Nemilia workflow editor — live DAG pipeline" width="98%" />
</div>

<br/>

<div align="center">
  <img src="https://nemilia.com/screenshots/workflows.png" alt="Built-in pipeline templates" width="49%" />
  <img src="https://nemilia.com/screenshots/workflow_selection.png" alt="Workflow mode selector" width="49%" />
</div>

---

### Agent Team

<div align="center">
  <img src="https://nemilia.com/screenshots/Agents.png" alt="Nemilia built-in agents — SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION" width="49%" />
  <img src="https://nemilia.com/screenshots/Agents_new.png" alt="Build custom agents" width="49%" />
</div>

---

### AI Providers & WebLLM Offline

<div align="center">
  <img src="https://nemilia.com/screenshots/AI_Provider.png" alt="AI provider configuration — cloud and local" width="49%" />
  <img src="https://nemilia.com/screenshots/webgpu.png" alt="WebLLM offline browser AI" width="49%" />
</div>

---

### Connections — Web Search & Image Generation

<div align="center">
  <img src="https://nemilia.com/screenshots/connections.png" alt="Web search and image generation connections" width="98%" />
</div>

---

## Three Ways to Run

| Mode | Setup | Privacy |
|---|---|---|
| ☁️ **Cloud API** | Use your existing OpenAI, Anthropic, Groq, Gemini, or OpenRouter API key | Keys encrypted AES-256, never leave your browser |
| 🖥️ **Local Server** | Point at your running Ollama, Jan, or LM Studio instance | 100% on-device, any installed model |
| 🔋 **Browser Offline** | Load Llama, Phi, Qwen, or Gemma via WebLLM — no key needed | Zero internet after first model download |
| 🔌 **Custom API** | Connect any OpenAI-compatible endpoint — LMDeploy, vLLM, Together, Fireworks, etc. | Your endpoint, your keys, full control |

Nemilia adapts to whatever setup you already have.

---

## Core Concepts

**Agents** are specialist AI personas. Each has a name, role, system prompt, optional model override, and a **per-agent temperature** setting (0.0–2.0) that controls response creativity independently from other agents. SCOUT researches, LENS analyses, QUILL writes, FORGE reviews, WEAVE synthesises, NEXUS searches the web, and VISION generates visuals. You can create unlimited custom agents for any domain.

**Workflows** are ordered pipelines of agents with a default **prompt template** (using `{{placeholders}}`). A workflow defines which agents run, in what order, and with what settings (validation, memory injection, HITL checkpoints, DAG mode). Selecting a workflow auto-fills the Compose textarea with its template and shows the live pipeline diagram in the toolbar. Nemilia ships with two built-in workflows: "Research Suite" (5 agents) and "Web Research Suite" (4 agents with live search).

**DAG Execution** runs agents in dependency-staged groups rather than one-by-one. Search agents run first (Stage 1), analysis agents run in parallel (Stage 2), synthesis agents run last (Stage 3). This is faster and respects API rate limits.

**Orchestrator** is a hidden LLM call that manages the entire pipeline. The **Advanced Orchestrator** mode enables richer decomposition: each agent receives a customized sub-task briefing, outputs are scored 1–10 with detailed rationale, and failed steps are retried with targeted improvement prompts.

**HITL (Human-in-the-Loop)** pauses the pipeline at flagged agents with an optional **audio alert**, presenting the output for human review with three actions: approve, edit, or send feedback for a re-run.

**RAG (Retrieval-Augmented Generation)** chunks uploaded documents and retrieves the most relevant passages for each query using a hybrid of semantic vector search (Transformers.js embeddings, 384 dimensions) and BM25 keyword matching (60/40 weighting). Documents can be bulk-imported via **folder scanning** (supports PDF, DOCX, TXT, MD, CSV, JSON, HTML, JS, TS, PY).

**Memory** is a persistent key-value store with two independent toggles: **Memory Writes** (whether agents can write new memories) and **Memory Injection** (whether stored memories are injected into agent context). Both are configurable globally in Settings and can be overridden per-workflow.

**Cost Tracking** shows a live **Est. Cost** counter during every run. Token counts and dollar estimates update in real-time as each agent streams, giving you instant visibility into API spend.

---

## Feature Overview

### Chat Mode
- Persistent multi-turn conversations stored in IndexedDB alongside workspace data
- Full streaming with real-time token rendering for all supported providers
- Automatic RAG context injection from active documents (hybrid vector + BM25)
- Session memory context automatically included in every message (when Memory Injection is on)
- **Web Search toggle** — click **Web Search** in the chat context bar to enable live web search on any message; only appears when a search provider is configured
- Conversation list with timestamps, message counts, and one-click deletion
- Auto-titling via LLM after first exchange
- Memory extraction from assistant responses (`MEMORY[key]: value` syntax)
- Keyboard shortcut: `Ctrl/⌘ + Enter` to send

### Compose & Workflow Mode
- **Workflow selector** — choose any workflow from the dropdown; the compose textarea auto-fills with the workflow's prompt template
- **Inline pipeline diagram** — live SVG DAG diagram appears to the right of the toolbar when a workflow is selected; auto-opens, click to collapse/expand, clears on "Direct prompt"
- **Real-time cost tracking** — token count and estimated dollar cost displayed live during every run
- **Executing badge** — live status indicator updates as each agent completes
- **Saved prompt chips** — click any saved template to instantly load it into the compose area
- **Context docs** — attach specific documents from your workspace to any run
- **Predictive Execution Engine** — pre-run complexity scoring (🟢/🟡/🔴), ambiguity flags, estimated runtime, and HITL suggestions shown before the pipeline fires

### Auto Workflow (AI Agent Routing)
- Select "🤖 Auto (AI picks agents)" from the Compose dropdown
- Orchestrator analyses your prompt and selects 1–5 agents from your library
- Agents are ordered logically (research → analysis → writing → synthesis)
- Shows routing rationale before launching the pipeline
- Runs through the full pipeline: DAG execution, validation, HITL, scoring, synthesis
- No manual workflow creation needed for ad-hoc tasks

### Agents & Orchestration
- 7 built-in specialist agents: SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION
- Custom agent creation with name, role, icon, colour, full system prompt, and model override
- **Per-agent temperature control** (0.0–2.0) — set creativity independently per agent; FORGE uses low temperature for consistent review, QUILL uses higher for creative writing
- **Advanced Orchestrator mode** — richer agent briefings, detailed quality rationale, targeted retry prompts; enable in Settings → Advanced: Orchestrator
- DAG-staged parallel execution — independent agents run simultaneously, reducing total run time
- Orchestrator validation: quality scoring 1–10, automatic retry on scores below threshold (up to 2 attempts)
- Session memory continuity — prior context injected into orchestrator on page reload

### Human-in-the-Loop
- Per-agent and per-workflow HITL checkpoints
- Three review actions: approve, inline edit, or feedback-driven re-run
- Amber-pulsing visual indicator while paused
- **Audio alert** — optional sound notification when execution pauses at a HITL checkpoint; toggle in Settings
- Unlimited feedback loops per checkpoint

### Workflow Builder
- Drag-and-drop agent reordering with live SVG flow diagram preview
- Inline HITL toggle per agent card
- **Prompt template** field — define a default prompt with `{{placeholder}}` variables that auto-fill the Compose textarea on workflow selection
- Configurable per workflow: orchestrator validation, DAG mode, memory injection, memory writes, SLM compression
- DAG stage assignment per agent (controls parallel grouping)

### Document RAG
- Upload **PDF, DOCX, TXT, MD, CSV** via drag-and-drop or file picker
- **Folder scan** — click 📂 Scan folder to bulk-import from a directory; supports `.md .txt .csv .json .html .pdf .js .ts .py .docx`
- Automatic 384-dimensional vector embeddings via Transformers.js (`all-MiniLM-L6-v2`)
- Hybrid search: 60% cosine vector similarity + 40% BM25 keyword matching
- 12,000-character context budget distributed proportionally across active documents
- Embeddings persist in IndexedDB — survive page refreshes and browser restarts
- Per-run document selection via 📎 Choose docs in the Compose toolbar

### Web Search
- 4 providers: Brave Search, Serper (Google results), Tavily AI, SearXNG (self-hosted)
- NEXUS agent runs first in DAG, passes cited findings to all downstream agents
- Inline `[Title](URL)` source citations in every output
- **Web Search toggle in Chat** — enable live search on individual chat messages without a workflow

### Image & Visual Generation
- VISION generates Chart.js charts, SVG diagrams, and HTML infographics (no API key needed)
- AI image generation via: **OpenAI DALL·E 3**, **Together AI (FLUX / Stable Diffusion)**, **xAI Aurora**, **Google Imagen 4**, **Stability AI SD3**, **Replicate (FLUX Pro + more)**, **Fal.ai (FLUX Dev)**
- Auto-prompting: orchestrator extracts `IMAGE_PROMPT:` directives from agent outputs
- Shimmer placeholder card appears instantly while images generate

### Browser-Native AI (WebLLM)
- Run 12 models entirely in-browser across all VRAM tiers (0.8 GB to 24 GB)
- Powered by MLC WebLLM with GPU (WebGPU) acceleration
- **HuggingFace model viewer** — browse and load any MLC-compiled model from the HuggingFace registry directly in the settings panel
- **Collapsible custom model URL** — paste a HuggingFace repo URL via the expandable ▸ Custom model URL field
- Models download once and cache in the browser for instant future loads
- Visual progress ring and percentage bar during download
- SLM prompt compression for better performance on small models
- **Unload Model** button frees GPU VRAM instantly

### Workspace & Storage
- **File System Access API** (Chrome/Edge): sync workspace to a real folder on disk; agents, prompts, and workflows saved as plain JSON/Markdown files
- **Folder scan** — bulk-import documents from any local directory
- Collapsible file browser in sidebar with per-folder expand/collapse
- Non-destructive saves: existing files never overwritten on reload
- IndexedDB fallback (Firefox/Safari) with localStorage as last resort
- **First-run experience** — setup wizard appears only once; `nem_initialized` flag prevents repeat prompts

### Memory System
- Persistent key-value store — agents write `MEMORY[key]: value`, all agents read
- **Memory Writes toggle** — independently enable/disable whether agents can write new memories (Settings → Memory Writes)
- **Memory Injection toggle** — independently enable/disable whether stored memories are injected into agent context (Settings → Memory Injection)
- Both toggles are per-session and per-workflow configurable
- Memory view in sidebar — browse, edit, and delete stored memories

### Templates & Output
- Reusable prompt templates with `{{placeholder}}` variables
- **Template gallery in-place refresh** — adding a template refreshes the gallery without closing the panel
- Workflow prompt templates auto-fill Compose on workflow selection
- PDF export of workflow results
- Markdown export and plain-text copy
- Full Markdown rendering: headers, code blocks, tables, lists, inline HTML
- **Real-time token count and Est. Cost** update live during every run
- Reasoning model support: `<think>` blocks stream as pulsing badges, collapse to toggle on completion

---

## MCP (Model Context Protocol) — Tool Execution

Nemilia supports **MCP servers** over both `streamableHttp` and `SSE` transports. Agents call external tools — filesystem, databases, APIs, code execution — in real time during a workflow run.

### How It Works

```
Agent prompt
→ LLM emits TOOLCALL{"tool":"read_file","path":"notes.txt"}
→ Nemilia calls mcpCallTool() on your MCP server
→ Result injected back into context
→ LLM continues with real data
```

### Connecting an MCP Server

```bash
npx -y supergateway --port 8000 --cors --outputTransport streamableHttp --stdio "npx -y @modelcontextprotocol/server-filesystem C:\mcptest"
```

**Connections → MCP Servers → + Add:** URL = `http://localhost:8000/mcp`

### MCP Troubleshooting

| Error | Fix |
|-------|-----|
| `406 Not Acceptable` | MCP header fix included from v1.22 |
| `CORS` | Add `--cors` to Supergateway |
| `0 tools` | URL: `/mcp` (streamableHttp) or `/sse` (SSE) |
| `Connection refused` | Check port 8000 is running |
| `Synthesis enable_thinking error` | Settings → uncheck "Reasoning / Think Tags" |

---

## Architecture

### Single-File Design

The entire application lives in one `.html` file — HTML, CSS, JavaScript, and embedded assets. No build step, no bundler, no framework.

| Library | Purpose | Loaded When | Size |
|---------|---------|-------------|------|
| PDF.js (Mozilla) | PDF text extraction | Document upload | ~400KB |
| WebLLM (MLC AI) | Browser-native LLM inference | WebLLM provider selected | ~200KB JS loader (models 0.8–24 GB) |
| Transformers.js (Xenova) | Vector embeddings for RAG | Document embedding | ~22MB model |
| Chart.js | Chart rendering in VISION | VISION output contains charts | ~65KB |

All libraries load on demand. WebLLM uses CDN fallbacks (esm.run → jsdelivr → esm.sh). PDF.js and Transformers.js load from a single pinned CDN URL each.

### Application Data Flow

```
User prompt + Docs + Memory
  └─▶ Orchestrator decomposition (per-agent briefings)
        └─▶ DAG Stage 1 — NEXUS (web search)
              └─▶ DAG Stage 2 — SCOUT, LENS, QUILL (parallel)
                    └─▶ DAG Stage 3 — FORGE (review)
                          └─▶ DAG Stage 4 — WEAVE (synthesis)
                                └─▶ Scoring + retry (if score < 6)
                                      └─▶ HITL checkpoint (if enabled)
                                            └─▶ Final synthesis → PDF / MD / TXT
```

### RAG Pipeline

```
Upload → Parser → Chunker → Transformers.js embeddings (384-dim) → IndexedDB
Query  → Cosine similarity (60%) + BM25 (40%) → top-K chunks → 12K char context
```

---

## Security & Privacy

**API keys** encrypted with AES-256-GCM before storage. PBKDF2 with 200,000 SHA-256 iterations per provider-specific salt. Keys only decrypted at the moment of an API call.

**Zero telemetry** — no analytics, no tracking, no beacons, no phone-home.

**What leaves your browser** (only when you initiate):
- LLM API calls to your configured provider
- Search API calls when NEXUS or Chat Web Search runs
- Image API calls when VISION generates images
- CDN library loads (PDF.js, WebLLM, Transformers.js, Chart.js) on first use

**WebLLM privacy** — when using the WebLLM provider, absolutely nothing leaves your browser after the initial model download.

---

## Provider Reference

| Provider | Recommended Model | Notes |
|----------|-------------------|-------|
| **Groq** | Llama 3.3 70B | Fastest free tier |
| **OpenRouter** | DeepSeek V3 | Access 200+ models |
| **Google Gemini** | Gemini 2.5 Flash | 1M context window |
| **Anthropic** | Claude Sonnet 4.6 | Best reasoning |
| **OpenAI** | GPT-4.1 | Widest tool support |
| **Mistral** | Mistral Large | European data residency |
| **DeepSeek** | DeepSeek V3 | Low cost |
| **Kimi (Moonshot)** | Kimi K2 | Long context |
| **xAI** | Grok 3 | Real-time data |
| **Ollama** | Any | Local, fully private |
| **LM Studio** | Any | Local GUI model manager |
| **Jan** | Any | Local, cross-platform |
| **Llamafile** | Any | Single-file local model |
| **WebLLM** | Qwen 2.5 7B ⭐ | In-browser, no API key |
| **Custom API** | Any | Any OpenAI-compatible endpoint |

---

## Quick Start

1. Download `Nemilia_V2_00.html`
2. Open in Chrome 121+, Edge 121+, Safari 17+, or Firefox 120+
3. On first open: click **🚀 Set Up Your AI Provider** and paste an API key (or connect Ollama/Jan/LM Studio, or load a WebLLM model)
4. Go to **Compose**, pick a workflow from the dropdown, and press **Ctrl+Enter**

The setup wizard only appears once — every subsequent open goes straight to your workspace.

---

## Tutorial: Connecting an AI Provider

### Cloud API
1. Click the gold pill in the header → select a provider → paste your API key → select a model → Save.

### Local Server (Ollama, Jan, LM Studio)
1. Start your local server → Click provider pill → select server type → enter endpoint URL → select model → Save.

### Browser AI (WebLLM)
1. Click provider pill → select **Browser AI (WebLLM)** → choose a model → click **Load model**.

### Switching providers
Click the provider pill anytime. Keys for all providers are remembered — switch instantly without re-entering credentials.

---

## Tutorial: Your First Workflow Run

1. Go to **Compose** in the sidebar.
2. Select **Research Suite** from the workflow dropdown. The textarea auto-fills with the workflow's prompt template and the pipeline diagram appears in the toolbar.
3. Edit the prompt to your topic.
4. Press **Ctrl+Enter**.
5. Watch SCOUT → LENS → QUILL → FORGE → WEAVE execute. Each agent streams live with a quality score.
6. The real-time **Est. Cost** counter updates as each agent completes.
7. Click **📄 PDF** to export the final report.

---

## Tutorial: Creating Custom Agents

1. **Agents → + New agent**
2. Set: Name, Role, Icon, Colour, System prompt
3. **Model override** — optional: use a different model for this agent than the global setting
4. **Temperature** (0.0–2.0) — lower for factual/review agents, higher for creative/writing agents
5. **⏸ HITL** — check to pause the pipeline at this agent for human review
6. Save → add the agent to any workflow

---

## Tutorial: Building Workflows with Drag-and-Drop

1. **Workflows → + New workflow**
2. Name it and write a **Prompt template** using `{{placeholders}}`
3. Add agents via the dropdown. Drag ⠿ handles to reorder. Toggle ⏸ HITL per agent.
4. Configure: validation, DAG mode, memory injection, memory writes, SLM compression
5. Save → appears in Compose dropdown immediately
6. Selecting the workflow auto-fills the textarea with the template and shows the inline pipeline diagram

---

## Tutorial: Human-in-the-Loop (HITL) Review

- **Enable globally** — Edit agent → check ⏸ HITL
- **Enable per workflow** — Workflow builder → toggle ⏸ on agent card
- **Audio alert** — Settings → enable HITL Sound Alert to get notified when execution pauses

**Actions when paused:**
- **✓ Approve** — continue pipeline as-is
- **✏️ Edit** — modify the output inline, then continue with your version
- **💬 Feedback** — type what to fix, re-run that agent, review again. Repeat as needed.

---

## Tutorial: Document RAG (Upload & Search)

1. **Documents** → drag-and-drop files (PDF, DOCX, TXT, MD, CSV) or click to browse
2. For bulk import: click **📂 Scan folder** — scans your workspace folder for all supported file types including `.docx`
3. Wait for the 🧠 Vector badge — embeddings are complete and persisted
4. In Compose: click **📎 Choose docs** to select documents for the run
5. Relevant chunks (up to 12,000 chars) are injected automatically into each agent's context

---

## Tutorial: Web Search with NEXUS

1. **Connections** → Search Provider → choose Brave / Serper / Tavily / SearXNG → paste key → Save
2. Add **NEXUS** as the first agent in your workflow (DAG Stage 1)
3. Run — NEXUS searches live, passes cited results to all downstream agents

**Chat web search:** click the Web Search button in the chat context bar to enable search for individual messages.

---

## Tutorial: Running Local Models (WebLLM)

1. Click provider pill → **Browser AI (WebLLM)**
2. Choose a model by VRAM tier:
   - ⚠️ Minimum (0.8–2 GB): SmolLM2 1.7B, Llama 3.2 1B
   - ✅ Recommended (4–8 GB): Qwen 2.5 7B ⭐, Llama 3.1 8B
   - 🔥 Enthusiast (12–24 GB): Llama 3.1 70B
3. Or browse the **HuggingFace model registry** directly in the panel for any MLC-compiled model
4. Or click **▸ Custom model URL** and paste a HuggingFace repo URL
5. Click **Load model** — progress ring shows download. Models cache locally after first download.
6. Click **Unload Model** to free GPU VRAM when switching providers

---

## Tutorial: Per-Agent Temperature

Temperature controls how creative or deterministic an agent's responses are.

- **0.0–0.3** — factual, consistent, best for review agents (FORGE) and structured output
- **0.5–0.7** — balanced, good for research and analysis (SCOUT, LENS)
- **0.8–1.2** — creative, good for writing agents (QUILL)
- **1.3–2.0** — highly experimental, use with caution

**To set:** Agents → edit any agent → Temperature field. The setting persists with the agent and overrides the global temperature for that agent's calls only.

---

## Tutorial: Memory System

**Writing memories:** Any agent outputs `MEMORY[key]: value` → stored persistently across sessions.

**Injecting memories:** When Memory Injection is on, all stored memories are prepended to each agent's context.

**Toggles (Settings):**
- **Memory Writes** — turn off to prevent agents from storing new memories during a run
- **Memory Injection** — turn off to run without memory context (useful for testing)

**Managing:** Sidebar → Memory → view, edit, delete any stored memory.

---

## Tutorial: Connecting a Custom API Provider

Any OpenAI-compatible endpoint works — vLLM, LMDeploy, Together AI, Fireworks, Perplexity API, etc.

1. Provider pill → **Custom API**
2. Enter: Display name, Endpoint URL, Model ID, optional API key
3. Set Context window and Max output if known
4. Save — available immediately as a provider option

---

## Tutorial: Workspace & File Management

1. Sidebar → **Open workspace** → select a folder (Chrome/Edge)
2. Agents, prompts, and workflows sync as JSON/Markdown — editable in any text editor
3. **Folder scan** (Documents) imports all supported file types from the workspace folder automatically
4. Files are never overwritten; Nemilia only writes new content

---

## Tutorial: Prompt Templates

1. **Prompts → + New template** → write with `{{placeholders}}` → Save
2. Click any saved prompt chip in Compose to load it instantly
3. Workflow prompt templates auto-fill Compose when that workflow is selected

---

## Tutorial: MCP Tool Execution

1. Start: `npx -y supergateway --port 8000 --cors --outputTransport streamableHttp --stdio "npx -y @modelcontextprotocol/server-filesystem C:\mcptest"`
2. **Connections → MCP Servers → + Add** → URL: `http://localhost:8000/mcp` → Test → Save
3. Create an agent with `TOOLCALL{...}` syntax in its prompt
4. Add to workflow → run

---

## Settings Reference

| Setting | Description |
|---------|-------------|
| Theme | Light / Dark / System |
| Reasoning / Think Tags | Stream `<think>` blocks as collapsible badges |
| Max Output Tokens | Upper ceiling for cloud provider responses |
| SLM Compression | Compress prompts for small local models |
| Memory Writes | Allow agents to write new memories during runs |
| Memory Injection | Inject stored memories into agent context |
| Orchestrator Validation | Score outputs 1–10, retry if below threshold |
| Advanced Orchestrator | Richer per-agent briefings and detailed scoring rationale |
| DAG Mode | Run independent agents in parallel |
| HITL Sound Alert | Audio notification when execution pauses at a checkpoint |

---

## Execution Flow

```
User prompt
  └─▶ Orchestrator decomposition → per-agent briefings
        └─▶ DAG Stage 1 — NEXUS (web search, if in workflow)
              └─▶ DAG Stage 2 — SCOUT, LENS, QUILL (parallel)
                    └─▶ DAG Stage 3 — FORGE (review)
                          └─▶ DAG Stage 4 — WEAVE (synthesis)
                                └─▶ Scoring + retry (score < 6)
                                      └─▶ HITL checkpoint (if enabled)
                                            └─▶ Final synthesis → output panel
                                                  └─▶ Export: PDF / MD / TXT / Copy
```

---

## Browser Compatibility

| Browser | Version | Notes |
|---------|---------|-------|
| Chrome | 121+ | Full support including WebLLM, File System API |
| Edge | 121+ | Full support including WebLLM, File System API |
| Safari | 17+ | Full support including WebLLM (WebGPU); File System API limited |
| Firefox | 120+ | Full support; no WebLLM (no WebGPU), no File System API |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/⌘ + Enter` | Run compose prompt / Send chat message |
| `Shift + Enter` | New line in compose / chat |
| `Escape` | Close modal |

---

## Changelog

### v2.0 — 2026-03-08

**Major UX Overhaul — Workflow Diagrams, Per-Agent Temperature, Memory Toggles, Folder Scan, Advanced Orchestrator, Real-Time Cost Tracking, WebLLM Viewer & More**

1. **Inline Workflow Diagram** — Live SVG pipeline diagram appears in the Compose toolbar to the right of "Choose docs" when a workflow is selected. Auto-opens on selection, shows DAG parallel groups, collapses/expands on click, clears on "Direct prompt". The diagram also re-renders in the execution output panel during runs.
2. **Per-Agent Temperature** — Each agent now has an independent temperature setting (0.0–2.0). Set low values on FORGE for consistent review, high values on QUILL for creative writing. Overrides the global temperature for that agent's calls only.
3. **Memory Writes Toggle** — New Settings toggle to independently enable/disable whether agents can write new memories during a run. Allows running workflows without modifying the memory store.
4. **Memory Injection Toggle** — New Settings toggle to independently enable/disable injection of stored memories into agent context. Useful for clean-room testing or privacy-sensitive runs.
5. **Folder Scan** — Bulk-import documents from a local directory. Scans for `.md .txt .csv .json .html .pdf .js .ts .py .docx`. The scan folder button tooltip lists all supported types and the scanner correctly parses Word documents.
6. **Advanced Orchestrator Mode** — New Settings option enables richer orchestrator behavior: detailed per-agent briefing flash during decomposition, structured quality rationale on scoring, targeted retry prompts for failed agents.
7. **Real-Time Token & Cost Tracking** — Live token count and estimated dollar cost (Est. Cost) update as each agent streams. Displayed in the compose run panel throughout execution.
8. **HuggingFace WebLLM Model Viewer** — Browse any MLC-compiled model from the HuggingFace registry directly in the WebLLM settings panel. Load directly or copy the URL into the custom model field.
9. **Collapsible WebLLM Custom URL** — The HuggingFace custom model URL field is hidden behind a collapsible "▸ Custom model URL" toggle to reduce visual clutter.
10. **Workflow Prompt Templates** — Workflows now carry a default prompt template (with `{{placeholders}}`). Selecting a workflow from the Compose dropdown auto-fills the textarea with the template.
11. **First-Run Gate** — Setup wizard uses `localStorage` flag (`nem_initialized`) so it only appears once. Returning users go straight to Compose with all data intact.
12. **HITL Sound Alert** — Optional audio notification when a HITL checkpoint pauses execution. Toggle in Settings.
13. **Executing Badge** — Live "Executing…" status badge in the compose output uses `appendChild` instead of `innerHTML` — survives streaming updates without flickering.
14. **Template Gallery Refresh** — Adding a prompt template refreshes the gallery in-place without closing the panel.
15. **Provider Connection Live Update** — Connecting or saving a provider while a workflow is selected immediately re-evaluates the Run button state — no need to re-select the workflow.
16. **Workflow Prompt Auto-Switch** — Selecting a different workflow from the dropdown always replaces the compose textarea with the new workflow's template.
17. **openCompose Diagram Clear** — Clicking "+ New prompt" now immediately clears the inline workflow diagram.
18. **Visual Close Button** — Close (✕) button on visual output cards is always visible with a proper hover state.

---

### v1.31 — 2026-03-07

**Decomposition UX, Custom Provider & Synthesis Reliability**

1. Per-agent briefing flash during orchestrator decomposition
2. Custom API provider slot (any OpenAI-compatible endpoint)
3. Local models now generate to EOS uncapped
4. Synthesis reliability restored for long pipelines
5. Orchestrator animated banner with live token count

---

### v1.30 — 2026-03-06

**Custom Provider, Local Context Detection, Orchestrator Banner**

1. Custom API Provider Slot
2. Orchestrator Animated Banner
3. LM Studio Native API Fallback
4. Manual Context Window Override
5. Pre-Run Context Warning
6. Think Toggle Fix
7. Version Strings wired to `VER` constant

---

### v1.29 — 2026-03-06

**Per-Provider Context Storage & WebLLM Engine Management**

1. Per-Provider Detected Context
2. Always Re-Detect on Save
3. WebLLM Engine Unload on Provider Switch
4. Migration Shim from v1.28

---

### v1.28 — 2026-03-05

**Synthesis Token Budget for Local Providers**

1. Local Synthesis Budget via `safeOutputBudget()`
2. WebLLM Stripped Synthesis Prompt

---

### v1.18 — 2026-03-03

**Context Safety, UX Polish & WebLLM Expansion**

1. Universal Context Budget Guard (`safeOutputBudget()`)
2. Live Synthesis Streaming
3. Animated synthesis placeholder and live token counter
4. Image Generation shimmer indicator
5. Agent Result Dropdowns with full Markdown
6. WebLLM expanded to 12 models across 4 VRAM tiers
7. Safari WebLLM support
8. Favicon added
9. `callAPIonce` timeout raised to 300 seconds

---

## License

Nemilia is released under the **Business Source License 1.1 (BSL 1.1)**.

- ✅ Free for personal, research, and non-commercial use
- ✅ Read, modify, and learn from the source
- ❌ No commercial use, resale, or SaaS deployment without a commercial license
- 🔄 Converts to MIT on 2030-02-27

For commercial licensing: [luis@nemilia.com](mailto:luis@nemilia.com)
