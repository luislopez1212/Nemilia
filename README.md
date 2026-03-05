<div align="center">
  <img src="https://nemilia.com/screenshots/full_logo.png" alt="Nemilia AI Workspace" width="340" />

  <h1>Nemilia — AI Workspace</h1>

  <p><strong>Your entire AI team. One file. Any provider.</strong></p>

  <p>
    Multi-agent orchestration &nbsp;·&nbsp; Document RAG &nbsp;·&nbsp; Live web research &nbsp;·&nbsp; Offline WebGPU<br/>
    Zero servers &nbsp;·&nbsp; Zero installs &nbsp;·&nbsp; 100% client-side
  </p>

  <p>
    <a href="https://nemilia.com">nemilia.com</a> &nbsp;·&nbsp;
    <a href="mailto:luis@nemilia.com">luis@nemilia.com</a>
  </p>

  <img src="https://img.shields.io/badge/version-1.21-gold" alt="version" />
  <img src="https://img.shields.io/badge/license-BSL_1.1-orange" alt="license" />
  <img src="https://img.shields.io/badge/backend-none-brightgreen" alt="no backend" />
  <img src="https://img.shields.io/badge/install-open%20HTML%20file-brightgreen" alt="install" />

</div>

---

**A browser-native AI workspace with multi-agent orchestration, human-in-the-loop review, semantic vector RAG, reasoning model support, and visual workflow design — all in a single HTML file with zero backend.**

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
  - [Auto Workflow](#auto-workflow-ai-agent-routing)
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
  - [Running Local Models (WebGPU)](#tutorial-running-local-models-webgpu)
  - [Workspace & File Management](#tutorial-workspace--file-management)
  - [Prompt Templates](#tutorial-prompt-templates)
  - [Memory System](#tutorial-memory-system)
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

At its core, Nemilia lets you define **specialist AI agents** — each with a distinct role, personality, and system prompt — then wire them into **pipelines called workflows**. When you run a workflow, Nemilia orchestrates the agents in dependency order: a research agent gathers information, an analyst extracts insights, a writer produces content, a reviewer critiques it, and a synthesizer merges everything into a polished final report. Each agent's output is scored for quality and automatically retried if it falls short.

This is not a chatbot. It is a structured AI workspace where multiple models collaborate on complex tasks with human oversight at every stage. (Though it does have a great chat mode too.)

### What Can You Do With It?

- **Chat** — persistent multi-turn conversations with streaming, document context, memory injection, and live web search. Conversations auto-title and persist across sessions.
- **Research reports** — SCOUT researches a topic, LENS analyses findings, QUILL writes the report, FORGE reviews it, WEAVE synthesizes everything into an executive summary. Five agents, one click.
- **Auto workflows** — describe your task and the AI orchestrator selects the right agents, orders them logically, and runs the pipeline automatically. No manual workflow setup needed.
- **Document Q&A** — upload a 200-page PDF, ask questions, and get answers grounded in specific passages with hybrid semantic + keyword search.
- **Live web research** — NEXUS searches the internet in real-time, then downstream agents process and synthesize the results with source citations.
- **Visual content** — VISION generates Chart.js charts, SVG diagrams, HTML infographics, and (optionally) AI-generated images from DALL·E, FLUX, Stable Diffusion, and more.
- **Offline AI** — run Llama, Phi, Qwen, or Gemma directly in your browser via WebGPU. No API key, no server, no internet after the initial model download.
- **Review and steer** — pause the pipeline at any agent with human-in-the-loop checkpoints. Approve the output, edit it inline, or send feedback to re-run that step.

### What Makes This Different?

| Feature | Nemilia | Typical AI Chat | AI Platform (Langchain, etc.) |
|---------|---------|-----------------|-------------------------------|
| Setup | Open an HTML file | Create account | Install Python, Docker, etc. |
| Chat | Persistent with RAG + memory + web search | Basic chat | Requires custom code |
| Multi-agent | Built-in orchestrator + auto-routing | Single model | Requires custom code |
| Human review | One-click HITL | None | Custom implementation |
| Data privacy | 100% client-side | Data on their servers | Varies |
| Document search | Hybrid vector + BM25 | Upload & hope | Vector DB setup |
| Provider lock-in | Any provider, swap anytime | Locked to one | Configurable but complex |
| Offline mode | WebGPU in-browser | No | No |

---

## Why It Exists

Most AI tools require you to trust a platform with your data, pay for a subscription, and accept whatever interface they provide. Nemilia takes a different approach:

- **Zero infrastructure** — no Docker, no Python environment, no `npm install`. One HTML file, any browser.
- **You own the runtime** — the code is open, readable, and runs on your machine. Nothing is obfuscated or phoned home.
- **Provider-agnostic** — switch between OpenAI, Anthropic, Groq, a local Ollama server, or in-browser WebGPU with a dropdown change. Your workflows don't lock you in.
- **Offline-capable** — with WebGPU and cached documents, Nemilia works without internet after initial setup.
- **Workspace portability** — sync to a local folder and your agents, prompts, and workflows become plain JSON and Markdown files you can version-control, share, or edit in any text editor.

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

### AI Providers & WebGPU Offline

<div align="center">
  <img src="https://nemilia.com/screenshots/AI_Provider.png" alt="AI provider configuration — cloud and local" width="49%" />
  <img src="https://nemilia.com/screenshots/webgpu.png" alt="WebGPU offline browser AI" width="49%" />
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
| 🔋 **Browser Offline** | Load Llama, Phi, Qwen, or Gemma via WebGPU — no key needed | Zero internet after first model download |

Nemilia adapts to whatever setup you already have.

---

## Core Concepts

**Agents** are specialist AI personas. Each has a name, role, system prompt, and optional model override. SCOUT researches, LENS analyses, QUILL writes, FORGE reviews, WEAVE synthesises, NEXUS searches the web, and VISION generates visuals. You can create unlimited custom agents for any domain.

**Workflows** are ordered pipelines of agents. A workflow defines which agents run, in what order, and with what settings (validation, memory injection, HITL checkpoints). Nemilia ships with two defaults: "Research Suite" (5 agents) and "Web Research Suite" (4 agents with live search).

**DAG Execution** runs agents in dependency-staged groups rather than one-by-one. Search agents run first (Stage 1), analysis agents run in parallel (Stage 2), synthesis agents run last (Stage 3). This is faster and respects API rate limits.

**Orchestrator** is a hidden LLM call that runs before and after each agent. It decomposes the user's prompt into agent-specific sub-tasks, scores each agent's output (1–10), triggers retries on low scores, and produces the final synthesis.

**HITL (Human-in-the-Loop)** pauses the pipeline at flagged agents, presenting the output for human review with three actions: approve, edit, or send feedback for a re-run.

**RAG (Retrieval-Augmented Generation)** chunks uploaded documents and retrieves the most relevant passages for each query using a hybrid of semantic vector search (Transformers.js embeddings, 384 dimensions) and BM25 keyword matching (60/40 weighting).

**Memory** is a persistent key-value store. Agents can write `MEMORY[key]: value` in their outputs. These facts are injected into all future agent prompts, building institutional knowledge across sessions.

---

## Feature Overview

### Chat Mode
- Persistent multi-turn conversations stored in IndexedDB alongside workspace data
- Full streaming with real-time token rendering for all supported providers
- Automatic RAG context injection from active documents (hybrid vector + BM25)
- Session memory context automatically included in every message
- **Web Search toggle** — click **Web Search** in the chat context bar to enable live web search on any message; button shows **Web Search ON** when active. The toggle only appears when a search provider is fully configured (provider selected AND API key saved in Connections). Switching or removing a provider automatically resets the toggle to prevent stale state.
- Conversation list with timestamps, message counts, and one-click deletion
- Auto-titling via LLM after first exchange (best-effort, non-blocking)
- Memory extraction from assistant responses (`MEMORY[key]: value` syntax)
- Keyboard shortcut: `Ctrl/⌘ + Enter` to send

### Auto Workflow (AI Agent Routing)
- Select "🤖 Auto (AI picks agents)" in the Compose dropdown
- Orchestrator analyses your prompt and selects 1–5 agents from your library
- Agents are ordered logically (research → analysis → writing → synthesis)
- Shows routing rationale before launching the pipeline
- Runs through the full existing pipeline: DAG execution, validation, HITL, scoring, synthesis
- Graceful fallback if routing JSON parsing fails (extracts agent names from text)
- No manual workflow creation needed for ad-hoc tasks

### Agents & Orchestration
- 7 built-in specialist agents (SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION)
- Custom agent creation with role prompts, icons, colours, and per-agent model overrides
- DAG-staged parallel execution with rate-limit awareness
- **Predictive Execution Engine** — pre-run complexity scoring (🟢/🟡/🔴), ambiguity flags, estimated runtime, and one-click HITL suggestions before any workflow fires
- **Session Memory Continuity** — snapshots last workflow, prompt, and run digests across sessions; prior context auto-injected into orchestrator on reload
- Orchestrator validation with quality scoring (1–10) and automatic retry (up to 2 attempts)
- Per-agent model overrides (use GPT-4 for analysis, Llama for drafts)

### Human-in-the-Loop
- Per-agent and per-workflow HITL checkpoints
- Three review actions: approve, inline edit, or feedback-driven re-run
- Amber-pulsing visual indicators during review
- Unlimited feedback loops: re-run with notes, review again, repeat

### Workflow Builder
- Drag-and-drop agent reordering with live SVG flow preview
- Inline HITL toggles per agent
- Configurable: validation, DAG mode, memory injection, SLM compression
- Prompt templates with `{{variable}}` placeholders

### Document RAG
- Upload PDF, DOCX, TXT, MD, CSV
- Automatic 384-dimensional vector embeddings via Transformers.js (`all-MiniLM-L6-v2`)
- Hybrid search: 60% cosine vector similarity + 40% BM25 keyword matching
- 12,000-character context budget distributed proportionally across active documents
- Embeddings persist in IndexedDB across page reloads

### Web Search
- 4 providers: Brave Search, Serper (Google results), Tavily AI, SearXNG (self-hosted)
- NEXUS agent runs first in DAG, passes cited findings to all downstream agents
- Inline `[Title](URL)` source citations in outputs
- **Web Search toggle in Chat** — enable live search on any individual chat message without needing a workflow

### Image & Visual Generation
- VISION generates Chart.js configs, SVG diagrams, and HTML infographics (no API needed)
- Optional AI image providers: **OpenAI DALL·E 3**, **Together AI (FLUX / Stable Diffusion)**, **xAI Aurora**, **Google Imagen 4**, **Stability AI SD3**, **Replicate (FLUX Pro + more)**, **Fal.ai (FLUX Dev)**
- Auto-prompting: orchestrator extracts `IMAGE_PROMPT:` directives from agent outputs

### Browser-Native AI (WebGPU)
- Run 12 models across all VRAM tiers — from 0.8 GB (Llama 1B) to 24 GB (Llama 70B) — entirely in the browser
- Powered by MLC WebLLM with GPU acceleration
- Models download once (0.8–24 GB depending on model) and cache in the browser for instant future loads
- Visual progress ring and percentage bar during download
- SLM prompt compression for better small-model performance
- Multiple CDN fallbacks for reliable library loading

### Workspace & Storage
- File System Access API (Chrome/Edge): sync workspace to a real folder on disk
- Collapsible file browser in sidebar with per-folder expand/collapse
- Non-destructive saves: existing files are **never overwritten** on reload
- IndexedDB fallback for Firefox/Safari with localStorage as last resort
- Plain JSON agents + Markdown prompts — editable in VS Code, Notepad, or any editor

### Memory, Templates & Output
- Persistent cross-session agent memory (agents write, all agents read)
- Reusable prompt templates with `{{placeholder}}` variables
- PDF export of workflow results
- Full Markdown rendering (headers, code blocks, tables, lists)
- Real-time token count, cost estimate, and elapsed time display

---

## MCP (Model Context Protocol) — Tool Execution

Nemilia supports **MCP servers** over both `streamableHttp` and `SSE` transports. This lets agents call external tools — filesystem, databases, APIs, code execution — in real time during a workflow run.

### How It Works

When an agent needs a tool it emits a `TOOLCALL{...}` block. Nemilia intercepts it, calls the MCP server, injects the result back into the agent context, and the LLM continues. All 100% client-side.

```
Agent prompt
→ LLM emits TOOLCALL{"tool":"read_file","path":"notes.txt"}
→ Nemilia calls mcpCallTool() on your MCP server
→ Result injected back into context
→ LLM continues with real data
```

### Connecting an MCP Server

**Recommended: Supergateway** (exposes any stdio MCP server to the browser)

```bash
# streamableHttp transport (recommended — v1.20 compatible)
npx -y supergateway --port 8000 --cors --outputTransport streamableHttp --stdio "npx -y @modelcontextprotocol/server-filesystem C:\\mcptest"
```

In Nemilia: **Connections → MCP Servers → + Add**

```
Name: filesystem
URL:  http://localhost:8000/mcp
```

Test → 14 tools found → Add

Ping button confirms connection is live.

### Building an MCP Agent

MCP tools are capabilities any agent can call. Create an agent that knows how to use them.

**Agents → New Agent:**

```
Name: FILES
Role: File System Operations
```

**Prompt:**

```
You are a file system assistant with access to MCP tools.
To read/list/write files, emit TOOLCALL:

TOOLCALL{"tool":"list_directory","path":"C:\\mcptest"}
TOOLCALL{"tool":"read_file","path":"C:\\mcptest\\README.md"}

Confirm what you found after each tool call.
```

### Example Workflows

**File Reader (single agent):**
```
Workflow: FILES only
Input: "List files in C:\mcptest and read README.md"
```

**Research → Save (multi-agent):**
```
Stage 1: NEXUS (web search)
Stage 2: QUILL (write report)
Stage 3: FILES (save to disk)
```

FILES prompt addition:
```
After QUILL content, save with:
TOOLCALL{"tool":"write_file","path":"C:\mcptest\report.md","content":"<paste>"}
```

### MCP Troubleshooting

| Error | Fix |
|-------|-----|
| `406 Not Acceptable` | Use Nemilia v1.20 (MCP header fix) |
| `CORS` | Add `--cors` to Supergateway |
| `0 tools` | URL: `/mcp` (streamableHttp) or `/sse` (SSE) |
| `Connection refused` | Check port 8000 terminal |
| `Synthesis enable_thinking error` | Settings → uncheck "Reasoning / Think Tags" |

---

## Architecture

### Single-File Design

The entire application — HTML structure, CSS styling, JavaScript logic, and embedded SVG/base64 assets — lives in one `.html` file (~5,700 lines). There is no build step, no bundler, no transpiler, and no framework dependency. You can read every line of code by opening the file in a text editor.

External libraries are loaded from CDNs at runtime only when their feature is used:

| Library | Purpose | Loaded When | Size |
|---------|---------|-------------|------|
| PDF.js (Mozilla) | PDF text extraction | Document upload | ~400KB |
| WebLLM (MLC AI) | Browser-native LLM inference | WebGPU provider selected | ~200KB |
| Transformers.js (Xenova) | Vector embeddings for RAG | Document embedding | ~22MB model |
| Chart.js | Chart rendering in VISION | VISION output contains charts | ~65KB |

All libraries load from multiple CDN fallbacks (jsdelivr, esm.run, esm.sh) for reliability. If one CDN is blocked or slow, the next is tried automatically.

### Application Data Flow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                              BROWSER                                    │
│                                                                         │
│  ┌──────────┐     ┌──────────────┐     ┌──────────────────────────────┐ │
│  │  User     │────▶│  Orchestrator │────▶│  Agent Pipeline              │ │
│  │  Prompt   │     │  (decompose   │     │                              │ │
│  │  + Docs   │     │   + score     │     │  Stage 1: NEXUS (web search) │ │
│  │  + Memory │     │   + retry)    │     │  Stage 2: SCOUT, LENS, QUILL │ │
│  └──────────┘     └──────────────┘     │  Stage 3: WEAVE (synthesis)   │ │
│                                         │  Stage 4: VISION (visuals)    │ │
│                                         └─────────────┬────────────────┘ │
│                                                       │                  │
│                          ┌────────────────────────────┤                  │
│                          │                            │                  │
│                          ▼                            ▼                  │
│                   ┌─────────────┐            ┌──────────────┐            │
│                   │  Validation  │            │   HITL        │            │
│                   │  Score 1–10  │            │   Review      │            │
│                   │  Auto-retry  │            │   ✓ Approve   │            │
│                   │  if < 6      │            │   ✏️ Edit     │            │
│                   └──────┬──────┘            │   💬 Feedback │            │
│                          │                   └───────┬──────┘            │
│                          ▼                           ▼                   │
│                   ┌──────────────────────────────────────┐               │
│                   │           Final Synthesis             │               │
│                   │    Markdown + Charts + Images + PDF   │               │
│                   └──────────────────────────────────────┘               │
│                                                                         │
│  ┌────────────────────────────────────────────────────────────────────┐  │
│  │                        STORAGE LAYER                               │  │
│  │  Tier 1: File System Access API (Chrome/Edge)                     │  │
│  │  Tier 2: IndexedDB                                                │  │
│  │  Tier 3: localStorage (fallback)                                  │  │
│  └────────────────────────────────────────────────────────────────────┘  │
│                                                                         │
│  ┌────────────────────────────────────────────────────────────────────┐  │
│  │  LLM: Groq / OpenAI / Anthropic / Gemini / Kimi / DeepSeek / ... │  │
│  │  Search: Brave / Serper / Tavily / SearXNG                        │  │
│  │  Images: DALL·E / FLUX / Aurora / Imagen 4 / SD3 / Replicate /   │  │
│  │          Fal.ai                                                    │  │
│  │  Local: Ollama / LM Studio / Jan / WebGPU (browser)               │  │
│  └────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

### RAG Pipeline Architecture

```
Document Upload → Parser → Chunker → Transformers.js embeddings (384-dim)
                                           │
                                     IndexedDB (Float32 arrays, persist forever)
                                           │
User Query ──▶ Cosine similarity (60%) ──┐
           ──▶ BM25 keyword search (40%) ─┴──▶ Hybrid-ranked top-K chunks
                                                      │
                                           Injected into agent context (12K char budget)
```

### How the Orchestrator Works

The orchestrator is not a visible agent — it's an automated LLM call that manages the pipeline:

1. **Decomposition** — before agents run, the orchestrator receives the user's prompt and outputs a JSON plan assigning each agent a specific sub-task.
2. **Execution** — agents run in DAG-staged order. Each receives its sub-task + outputs from prior agents + document context + memories.
3. **Validation** — after each agent, the orchestrator scores the output (1–10) based on completeness, accuracy, and relevance. Scores below 6 trigger automatic retries with a "improve on these issues" prompt injection.
4. **Synthesis** — after all agents complete, the orchestrator produces a final merged output combining all agent contributions.

---

## Security & Privacy

### Threat Model

Nemilia is designed for a single user running it on their own machine. The threat model assumes:

- You trust your browser (Chrome, Edge, Firefox, Safari)
- You trust the LLM provider you connect (your prompts are sent to them)
- You do not share your browser profile with untrusted users
- The HTML file itself has not been tampered with

### API Key Protection

**Encryption at rest** — every API key is encrypted with **AES-256-GCM** before storage. The encryption key is derived via **PBKDF2 with 200,000 iterations** of SHA-256 using a provider-specific salt.

**Storage isolation** — encrypted key blobs are stored in IndexedDB (primary) with localStorage fallback. Keys are **never written to disk as plaintext**, even when using the File System API workspace sync.

**Transmission scope** — a key is decrypted only at the moment of an API call and sent exclusively to the endpoint URL hard-coded for that provider. Keys are never sent to any Nemilia server (there is none), analytics service, or third-party endpoint.

**No cross-provider leakage** — each provider's key is stored and encrypted independently.

### Data Privacy

**Zero telemetry** — Nemilia contains no analytics scripts, no tracking pixels, no beacons, and no phone-home code of any kind.

**Client-side processing** — document parsing, chunking, embedding, BM25 scoring, vector search, memory management, workflow orchestration, Markdown rendering, chart generation, and PDF export all happen locally in your browser.

**What leaves your browser** (only when you initiate it):
- **LLM API calls** — prompts sent to your configured provider over HTTPS
- **Search API calls** — queries sent to your configured search provider (Brave, Serper, Tavily, or SearXNG) when NEXUS runs or Web Search is active in Chat
- **Image API calls** — prompts sent to your configured image provider when VISION generates AI images
- **CDN library loads** — PDF.js, WebLLM, Transformers.js, and Chart.js fetched from public CDNs on first use

### Content Security

- **XSS prevention** — all user-facing content sanitised through the `esc()` function; agent outputs rendered as Markdown, never raw HTML
- **CSP meta tag** — Content Security Policy restricts script sources
- **Style injection prevention** — colour values from user input sanitised
- **Non-destructive workspace** — existing files never overwritten on reload

### WebGPU / Local Model Privacy

When using the WebGPU provider, **absolutely nothing leaves your browser** after the initial model download. All inference runs on your local GPU — true offline AI.

---

## Provider Reference

| Provider | Recommended Model | Setup Link |
|----------|-------------------|------------|
| **Groq** | Llama 3.3 70B | [console.groq.com](https://console.groq.com) |
| **OpenRouter** | DeepSeek V3 | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **Google Gemini** | Gemini 2.5 Flash | [aistudio.google.com](https://aistudio.google.com/apikey) |
| **Anthropic** | Claude Sonnet 4 | [console.anthropic.com](https://console.anthropic.com) |
| **OpenAI** | GPT-4.1 | [platform.openai.com](https://platform.openai.com) |
| **Mistral** | Mistral Large | [console.mistral.ai](https://console.mistral.ai) |
| **DeepSeek** | DeepSeek V3 | [platform.deepseek.com](https://platform.deepseek.com) |
| **Kimi (Moonshot)** | Kimi K2 / K2.5 | [platform.moonshot.ai](https://platform.moonshot.ai) |
| **xAI** | Grok 3 | [console.x.ai](https://console.x.ai) |
| **Ollama** | Any | [ollama.com](https://ollama.com) |
| **LM Studio** | Any | [lmstudio.ai](https://lmstudio.ai) |
| **Jan** | Any | [jan.ai](https://jan.ai) |
| **Llamafile** | Any | [Mozilla Llamafile](https://github.com/Mozilla-Ocho/llamafile) |
| **WebGPU** | Qwen 2.5 7B ⭐ | Built-in (Chrome 121+, Edge 121+, Safari 17+) |

---

## Quick Start

1. Download `Nemilia.html` from this repo
2. Open it in Chrome 121+, Edge 121+, Safari 17+, or any modern browser
3. Click **🚀 Set Up Your AI Provider** — paste any API key, or connect your local Ollama/Jan/LM Studio server
4. Go to **Compose**, type a prompt, and press **Ctrl+Enter**

That's it. Everything saves automatically in your browser.

---

## Tutorial: Connecting an AI Provider

Nemilia needs an LLM to power its agents. You have three options: cloud API (fastest setup), local server (Ollama/Jan/LM Studio), or in-browser (WebGPU, no account needed).

### Cloud API (recommended for beginners)

1. **Click the gold pill** in the header that says "🚀 Set Up Your AI Provider".
2. The provider modal opens showing a grid of providers. **Click any provider** to select it.
3. If you don't have an account yet, click the blue setup link to create one and generate an API key.
4. **Paste your API key** in the input field and click **Save key**.
5. **Select a model** from the dropdown.
6. Click **Save** at the bottom. The header pill turns green and shows your provider name.

**Tip:** Your API key is encrypted with AES-256-GCM before storage. It never leaves your browser except when sent to the provider's API endpoint.

### Local Server (Ollama, Jan, LM Studio)

1. Start your local server (Ollama, Jan, or LM Studio) and load a model.
2. Click the provider pill → select your local server type.
3. Enter your local endpoint URL (e.g. `http://localhost:11434` for Ollama).
4. Select a model from the list of locally installed models.
5. Click **Save**. All inference runs entirely on your machine.

### Switching providers later

Click the provider pill in the header anytime. Your keys for all providers are remembered — you can switch instantly.

---

## Tutorial: Your First Workflow Run

1. Navigate to **Compose** (left sidebar, top item).
2. In the toolbar above the text area, find the **workflow dropdown** (says "Direct prompt" by default). Select **"Research Suite"**.
3. Type a research topic in the text area.
4. Press **Ctrl+Enter** or click **Run**.
5. Watch the pipeline execute: SCOUT researches → LENS analyses → QUILL writes → FORGE reviews → WEAVE synthesises.
6. Each agent's output appears in a card with a quality score (1–10). The final synthesis appears at the bottom.
7. Click **📄 PDF** to download the report.

---

## Tutorial: Creating Custom Agents

1. Go to **Agents** in the left sidebar.
2. Click **+ New agent**.
3. Fill in: **Name**, **Role**, **Icon**, **Colour**, **System prompt**, and optionally a **Model override**.
4. Check **⏸ Requires human approval (HITL)** if you want to review this agent's output before the pipeline continues.
5. Click **Save agent**.

After saving, add the agent to any workflow via the workflow builder.

---

## Tutorial: Building Workflows with Drag-and-Drop

1. Go to **Workflows** → click **+ New workflow**.
2. Name your workflow and optionally write a default prompt template using `{{placeholders}}`.
3. Use the dropdown to add agents. Each appears as a draggable card.
4. **Grab the ⠿ handle** on any agent card and drag to reorder. The SVG flow preview updates in real-time.
5. Toggle **⏸ HITL** on any agent card to add a review checkpoint for that step.
6. Configure workflow settings (orchestrator validation, DAG mode, memory injection, SLM compression).
7. Click **Save workflow**. It appears in the Compose dropdown ready to use.

---

## Tutorial: Human-in-the-Loop (HITL) Review

### Enabling HITL

- **Per agent (global)**: Edit an agent → check "⏸ Requires human approval (HITL)".
- **Per workflow (override)**: In the workflow builder, click the ⏸ button on a specific agent card.

### The three actions during a paused run

**✓ Approve** — satisfied with the output. Click to continue the pipeline.

**✏️ Edit** — click to reveal an editable text area with the full output. Make changes, then click **✏️ Save edit**. The pipeline continues with your modified version.

**💬 Send Feedback** — type what's wrong or what you want changed. Click **💬 Re-run with feedback**. The agent re-runs with your feedback injected into its prompt, then pauses again for review. Loop as many times as needed.

---

## Tutorial: Document RAG (Upload & Search)

1. Go to **Documents** in the left sidebar.
2. **Drag and drop** files into the drop zone, or click to browse. Supported: PDF, DOCX, TXT, MD, CSV.
3. Nemilia parses, chunks, and generates vector embeddings automatically. A green **🧠 Vector** badge appears when complete.
4. In **Compose**, click **📎 Context** to select which documents to include.
5. Run your prompt. The most relevant chunks (up to 12,000 characters) are automatically injected into each agent's context.

Embeddings persist in IndexedDB — they survive page refreshes and browser restarts.

---

## Tutorial: Web Search with NEXUS

NEXUS is a specialist agent that searches the live web during workflow execution.

### Setting up web search

1. Go to **Connections** in the left sidebar.
2. Under **Search Provider**, choose one:
   - **Brave Search** — [brave.com/search/api](https://brave.com/search/api/)
   - **Serper** (Google results) — [serper.dev](https://serper.dev/)
   - **Tavily AI** — [tavily.com](https://tavily.com/)
   - **SearXNG** — self-hosted, no API key needed (enter your instance URL)
3. Paste your API key and click **Save**.

### Using NEXUS in a workflow

NEXUS is included in the "Web Research Suite" workflow by default. When a workflow runs with NEXUS:
1. NEXUS runs first (Stage 1 in DAG mode).
2. It generates search queries, retrieves results, and summarises findings with inline `[Title](URL)` citations.
3. Its output is passed to all downstream agents as additional context.

You can also add NEXUS to any custom workflow via the workflow builder.

---

## Tutorial: Using Web Search in Chat

Chat mode supports live web search on a per-message basis — no workflow or NEXUS agent required.

**Prerequisites:** A search provider must be configured in **Connections → Web Search** (Brave, Serper, Tavily, or SearXNG).

### How to use it

1. Go to **Chat** in the left sidebar and open or start a conversation.
2. Look for the **Web Search** button in the context bar just above the message input. This button only appears when a search provider is fully configured (provider selected AND API key saved).
3. Click it to toggle web search on — the button label changes to **Web Search ON**.
4. Type your message and send. Live search results are fetched and injected into the model's context before it responds.
5. Click **Web Search ON** again to turn it off and return to standard chat.

> **Note:** If you switch or remove your search provider in Connections, the toggle automatically resets to OFF. You won't see a phantom "ON" state for a provider that's no longer configured.

> **Tip:** Web Search in chat is best for factual, time-sensitive, or news-related queries. For deep multi-source research with citations and synthesis across multiple agents, use a workflow with NEXUS instead.

---

## Tutorial: Image Generation with VISION

### Code-based visuals (no API key needed)

VISION generates visual content as code that Nemilia renders in the browser:
- **Charts**: Chart.js configs (bar, line, pie, radar, doughnut, polarArea)
- **SVG diagrams**: process flows, architecture diagrams, comparisons
- **HTML infographics**: styled cards, dashboards, comparison tables

These work with any text provider — no image API required.

### AI-generated images (optional)

For photographic images, illustrations, and art, configure one of the supported providers in **Connections → Image Generation**:

| Provider | Models |
|----------|--------|
| OpenAI | DALL·E 3 |
| Together AI | FLUX, Stable Diffusion |
| xAI | Aurora |
| Google | Imagen 4 |
| Stability AI | SD3 |
| Replicate | FLUX Pro, and more |
| Fal.ai | FLUX Dev |

Paste the API key for your chosen provider and click **Save**. When VISION detects a visual request, it generates code-based visuals AND an AI image if a provider is configured.

---

## Tutorial: Running Local Models (WebGPU)

Run AI models entirely in your browser — no API key, no server, no internet after the first download.

### Requirements

- **Chrome 121+**, **Edge 121+**, or **Safari 17+** (WebGPU must be available)
- A GPU (integrated or dedicated)
- 0.8–24 GB of VRAM depending on model — each model shows its requirement in the selector

### Setup

1. Click the provider pill → select **Browser (WebGPU)**.
2. **Choose a model** from the dropdown:
   - ⚠️ **Llama 3.2 1B** (~0.8 GB VRAM) — fastest, minimal tasks
   - ⚠️ **Llama 3.2 3B** (~2.5 GB VRAM) — simple workflows
   - ⚠️ **SmolLM2 1.7B** (~1.2 GB VRAM) — ultra-light, utility only
   - ⚠️ **Gemma 2 2B** (~1.4 GB VRAM) — Google compact
   - ✅ **Phi 3.5 Mini** (~3.7 GB VRAM) — strong instruction following
   - ✅ **Qwen 2.5 3B** (~1.9 GB VRAM) — multilingual, fast
   - ✅ **Qwen 2.5 7B** ⭐ (~5.1 GB VRAM) — **recommended**, best quality/size
   - ✅ **Llama 3.1 8B** (~5.0 GB VRAM) — strong general purpose
   - ✅ **Mistral 7B** (~4.1 GB VRAM) — strong reasoning
   - ✅ **DeepSeek R1 7B** (~5.1 GB VRAM) — best for complex agent tasks
   - 🔥 **Gemma 2 9B** (~6.4 GB VRAM) — high quality, needs 8 GB card
   - 🔥 **Llama 3.1 70B** (~24 GB VRAM) — enthusiast, 24 GB+ GPU only
3. Click **⬇ Download & Load Model**.
4. The circular progress ring shows download percentage. **This is a one-time download** — the model is cached in your browser for future use.
5. Once loaded, the ring shows ✓ green and the header pill turns green.

### Important notes

- WebGPU models download from CDN servers on first use, then cache permanently.
- Enable **SLM mode** in workflow settings to compress prompts for better small-model performance.
- Quality is lower than cloud models (3B params vs 70B+), but it's completely private.

---

## Tutorial: Workspace & File Management

### Setting up a workspace folder (Chrome/Edge)

1. Click **Open workspace** in the sidebar footer.
2. The setup wizard appears. Click **Choose folder** and select or create a directory.
3. Click **Next** — Nemilia creates folders and writes default files. **Existing files are never overwritten.**

### The Files panel

Once connected, a **Files** section appears in the sidebar below Results:
- Click **▶ Files** to expand/collapse the entire file tree.
- Click any 📁 folder to expand/collapse it.
- Click any file to open it in the built-in text editor.
- Click **+** to create a new file.

### Storage badge

The header badge shows your active mode: **FS** (filesystem on disk), **IDB** (IndexedDB), or **LS** (localStorage fallback).

---

## Tutorial: Prompt Templates

1. Go to **Prompts** → click **+ New prompt**.
2. Fill in name, description, tags, and content. Use `{{double_braces}}` for variables:
   ```
   Generate a weekly status report for {{team_name}}.
   Key accomplishments: {{accomplishments}}
   Blockers: {{blockers}}
   ```
3. Click **Save prompt**.
4. In Compose, click a prompt chip below the toolbar. The template fills in with placeholders highlighted.

---

## Tutorial: Memory System

Any agent can write `MEMORY[key]: value` in its output:
```
MEMORY[company_founding]: Acme Corp was founded in 2019 by Jane Smith.
MEMORY[main_competitor]: Their primary competitor is GlobalTech Inc.
```

These are automatically extracted and stored. On future runs with memory enabled, all stored memories are injected into every agent's context.

Go to **Memory** in the left sidebar to view, edit, and delete stored key-value pairs. Use descriptive keys (`quarterly_revenue_2024` not just `revenue`) for clarity.

---

## Tutorial: MCP Tool Execution

MCP (Model Context Protocol) lets agents call external tools — read and write files, query databases, run code, hit APIs — in real time during a workflow run. Everything stays 100% client-side.

### Prerequisites

- Nemilia v1.20
- Node.js installed (for running Supergateway via `npx`)
- An MCP server to connect to (the filesystem server is used in this tutorial)
- A test folder for the filesystem server to access — create it now if it doesn't exist:
  ```bash
  mkdir C:\mcptest
  ```

---

### Step 1 — Start an MCP Server with Supergateway

Supergateway wraps any stdio-based MCP server and exposes it to the browser over HTTP. Open a terminal and run:

```bash
npx -y supergateway --port 8000 --cors --outputTransport streamableHttp --stdio "npx -y @modelcontextprotocol/server-filesystem C:\\mcptest"
```

- `--port 8000` — the local port Nemilia will connect to
- `--cors` — required so the browser can reach the server
- `--outputTransport streamableHttp` — recommended transport (v1.20 compatible)
- The final argument is the MCP server command — here the official filesystem server pointed at `C:\mcptest`

Leave this terminal running. You should see output confirming the server started on port 8000.

> **Other transports:** If you prefer SSE, replace `streamableHttp` with `sse` and use `/sse` as the URL path in the next step instead of `/mcp`.

---

### Step 2 — Connect the MCP Server in Nemilia

1. Go to **Connections** in the left sidebar.
2. Under **MCP Servers**, click **+ Add**.
3. Fill in:
   ```
   Name: filesystem
   URL:  http://localhost:8000/mcp
   ```
4. Click **Test**. You should see a tool count — e.g. **14 tools found**.
5. Click **Add** to save the connection.

The **Ping** button next to the saved server confirms the connection is live at any time.

> **0 tools?** Double-check the URL path — use `/mcp` for `streamableHttp` transport or `/sse` for SSE transport.

---

### Step 3 — Create an MCP Agent

MCP tools are available to any agent that knows how to emit `TOOLCALL` blocks. Create a dedicated agent:

1. Go to **Agents** → click **+ New agent**.
2. Fill in:
   ```
   Name:  FILES
   Role:  File System Operations
   Icon:  📁
   ```
3. Paste this system prompt:
   ```
   You are a file system assistant with access to MCP tools.

   To interact with files, emit a TOOLCALL on its own line:

   TOOLCALL{"tool":"list_directory","path":"C:\\mcptest"}
   TOOLCALL{"tool":"read_file","path":"C:\\mcptest\\notes.txt"}
   TOOLCALL{"tool":"write_file","path":"C:\\mcptest\\output.md","content":"Your content here"}

   After each tool call, describe what you found or confirm what was written before continuing.
   ```
4. Click **Save agent**.

> **How it works:** When the agent emits a `TOOLCALL{...}` line, Nemilia intercepts it, calls `mcpCallTool()` on your connected MCP server, injects the result back into the agent context, and the LLM continues with the real data.

---

### Step 4 — Run a Single-Agent File Workflow

The simplest use case — one agent, one task.

1. Go to **Workflows** → click **+ New workflow**.
2. Name it `File Operations` and add the **FILES** agent.
3. Save the workflow.
4. Go to **Compose**, select **File Operations** from the workflow dropdown.
5. Type a prompt:
   ```
   List all files in C:\mcptest and read the contents of README.md
   ```
6. Press **Ctrl+Enter** to run.

FILES will emit `TOOLCALL` blocks, receive the real directory listing and file contents, and produce a response grounded in your actual filesystem.

---

### Step 5 — Build a Multi-Agent Research → Save Workflow

Chain NEXUS (web search), QUILL (writing), and FILES (save to disk) for an end-to-end pipeline that writes results directly to your filesystem.

1. Go to **Workflows** → **+ New workflow**, name it `Research & Save`.
2. Add agents in this order:
   ```
   Stage 1: NEXUS   — live web research
   Stage 2: QUILL   — write the report
   Stage 3: FILES   — save to disk
   ```
3. Edit the **FILES** agent prompt to include:
   ```
   After receiving QUILL's report content, save it to disk:
   TOOLCALL{"tool":"write_file","path":"C:\\mcptest\\report.md","content":"<QUILL output here>"}
   Confirm the file was written successfully.
   ```
4. Save the workflow.
5. In **Compose**, run with a prompt like:
   ```
   Research the latest developments in quantum computing and save a summary report.
   ```

NEXUS fetches live results → QUILL writes the report → FILES saves `report.md` to `C:\mcptest`.

---

### Troubleshooting

| Symptom | Fix |
|---------|-----|
| `406 Not Acceptable` | Ensure you are on Nemilia v1.20 (MCP header fix) |
| `CORS error` in console | Add `--cors` flag to your Supergateway command |
| `0 tools found` | Check URL path: `/mcp` for streamableHttp, `/sse` for SSE |
| `Connection refused` | Verify the Supergateway terminal is still running on port 8000 |
| `Synthesis enable_thinking error` | Go to **Settings** → uncheck **Reasoning / Think Tags** |
| Tool result not injected | Ensure `TOOLCALL` is on its own line with no leading spaces |

---

## Settings Reference

The **Settings** page (`⚙ Settings` in the left sidebar) controls global defaults for all agents, workflows, and storage. Changes save instantly.

### AI Provider

A shortcut button that opens the provider configuration modal. See the [Provider Reference](#provider-reference) section for a full list of supported services.

### Defaults

#### System Prompt

A global default system prompt sent to the LLM before every conversation. Individual agents have their own system prompts that override this during workflow runs.

#### Max Output Tokens

| Default | Min | Max |
|---------|-----|-----|
| `4096` | `256` | `200000` |

Controls how many tokens the model is allowed to generate in a single response.

- **Recommended for workflows:** `4096`–`8192` for standard agents; `16000`+ for VISION with complex HTML infographics.
- **Recommended for chat:** `2048`–`4096` for most conversations.

#### Temperature

| Default | Min | Max | Step |
|---------|-----|-----|------|
| `0.7` | `0.0` | `1.0` | `0.05` |

| Value | Behaviour | Best for |
|-------|-----------|----------|
| `0.0` | Fully deterministic | Factual Q&A, code, structured JSON |
| `0.3` | Focused and consistent | Analysis, summarisation, FORGE |
| `0.7` *(default)* | Balanced creativity and coherence | General writing, research, chat |
| `1.0` | Maximum creativity | Brainstorming, creative writing, VISION |

#### Max Retries

| Default | Min | Max |
|---------|-----|-----|
| `3` | `1` | `8` |

How many times the orchestrator will automatically re-run an agent whose output scored below **6/10**.

#### DAG Stagger Delay

| Default | Min | Max | Step |
|---------|-----|-----|------|
| `600ms` | `0ms` | `5000ms` | `100ms` |

The delay inserted between DAG pipeline stages to avoid simultaneous API bursts.

- **0ms** — all agents fire simultaneously. Fastest, but likely to hit rate limits.
- **300–600ms** *(recommended)* — avoids rate limit errors on most providers.
- **1000ms+** — conservative pacing for providers with strict per-minute request limits.

**Tip:** If you see `429 Too Many Requests` errors, increase this value first.

### Storage

| Badge | Storage tier | Notes |
|-------|-------------|-------|
| **FS** | File System Access API | Chrome/Edge only. Workspace synced to a real folder on disk. |
| **IDB** | IndexedDB | Firefox/Safari fallback. No practical size limit. |
| **LS** | localStorage | Last-resort fallback. ~5MB limit. |

### Data

- **Export JSON** — downloads your entire workspace as a single `.json` file.
- **Import** — restores a workspace from a previously exported `.json` file.
- **Clear all data** — permanently deletes all workspace data (irreversible, confirmation required).

---

## Execution Flow

```
User Prompt
    │
    ▼
┌─────────────┐
│ ORCHESTRATOR │  ← Decomposes prompt into agent subtasks
└──────┬──────┘
       ▼
┌──────────────┐
│   NEXUS      │  ← Web search (Stage 1, if included)
└──────┬───────┘
       │  ⏸ HITL checkpoint (if enabled)
       ▼
┌──────────────────────────────────┐
│  SCOUT  │  LENS  │  QUILL       │  ← Analysis (Stage 2, parallel)
└──────────┬───────────────────────┘
           │  ⏸ HITL checkpoint (if enabled)
           ▼
┌──────────────┐
│    WEAVE     │  ← Synthesis (Stage 3)
└──────┬───────┘
       ▼
┌──────────────┐
│   VISION     │  ← Charts, diagrams, images (Stage 4)
└──────┬───────┘
       ▼
┌──────────────┐
│ ORCHESTRATOR │  ← Final synthesis + scoring
└──────┬───────┘
       ▼
   Final Output (Markdown + Charts + Images + PDF)
```

Each agent's output is scored 1–10. Scores below 6 trigger automatic retries (up to 2). HITL checkpoints pause for human review between stages.

---

## Browser Compatibility

| Feature | Chrome 121+ | Edge 121+ | Firefox | Safari |
|---------|-------------|-----------|---------|--------|
| Core functionality | ✅ | ✅ | ✅ | ✅ |
| File System API | ✅ | ✅ | ❌ (uses IDB) | ❌ (uses IDB) |
| WebGPU (local LLM) | ✅ | ✅ | ⚠️ limited | ✅ Safari 17+ |
| Vector RAG embeddings | ✅ | ✅ | ✅ | ✅ |
| PDF parsing | ✅ | ✅ | ✅ | ✅ |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Run prompt / Send chat message |
| `Shift + Enter` | New line in input |
| `Ctrl/⌘ + K` | Focus compose input |

---

## Changelog

### v1.21 — 2026-03-05

**Think Tag System Overhaul, Token Counter & Stability Fixes**

1. **Think Tag Toggle Now Works Everywhere** — Rewrote the reasoning/think tag pipeline so the Settings toggle is respected across all surfaces. Previously, workflow agent card outputs, HITL re-runs, and MCP follow-up streams bypassed `processThinkTags` entirely and used bare `stripThinkingTags`, silently erasing reasoning content regardless of user preference. All agent card outputs now route through `processThinkTags` + `renderComposeThinker`, showing the collapsible reasoning badge when the toggle is on.
2. **Provider Compatibility Fix (Groq, xAI, Mistral, Kimi, Ollama, all OpenAI-compatible)** — Removed `enable_thinking` and `thinking: {type:'disabled'}` parameters that were being sent to every OpenAI-compatible provider during synthesis. These parameters are only valid on DeepSeek Reasoner and caused 400 errors on all other providers. The `disableThinking` parameter has been removed from `streamAPI` entirely — the display layer handles all think-tag cleanup.
3. **Token Counter Active From First API Call** — The run token counter previously showed 0 until agents began streaming, because decomposition and validation calls used `callAPIonce` which had no connection to `updateStats`. Added optional `onTokens` callback to `callAPIonce`; decomposition and each validation call now pass `updateStats`, so the counter increments from the moment orchestration begins.
4. **Agent Inactivity Timeout Raised to 180s** — The watchdog that aborts a run when an agent stream goes silent was raised from 60 seconds to 180 seconds for all cloud and local server providers. 60s was too aggressive — free-tier providers, large RAG context, and peak-load conditions can legitimately delay the first token by 60–90 seconds, causing valid runs to abort. WebGPU remains at 600 seconds.
5. **`streamAPI` Returns Raw Content** — Previously stripped think tags from its return value regardless of context, silently eating reasoning content for any caller using the return. Now returns raw content; display layer owns all cleanup.
6. **Settings Checkboxes Now Sync on Load** — Think-tag toggle checkboxes always showed unchecked on first visit even though the strip behavior was active (default is `true`). `loadThinkSettings()` now runs during `init()` after `renderAll()` to sync both checkboxes to their actual stored state.

### v1.20 — 2026-03-04

**Bug Fixes & State Management**

1. **SSE Parser `break outer` Fix** — The Server-Sent Events stream reader now correctly uses `break outer` when it encounters `data: [DONE]`, exiting the enclosing `while` loop rather than only the inner `for` loop. Previously this could produce a rare double-completion event on providers that send a trailing empty chunk after `[DONE]`.
2. **`directConvoHistory` Promoted to Module Scope** — The direct-prompt follow-up conversation history was a local variable inside `openCompose()`, meaning `openCompose()` could never actually clear it between runs. Variable now lives at module level and is properly reset on navigation.
3. **Double-Send Guard in Follow-Up Input** — Added an in-flight guard to the follow-up streaming path. Pressing Enter while a reply was streaming would fire a second overlapping API call; this no longer happens.
4. **Chat `AbortError` History Poisoning Fix** — When a user clicked Stop during a chat stream, the partial/empty response was being pushed into `chatHistory`, which then corrupted the next message's context. Abort paths now skip history mutation entirely.
5. **Auto-Route Neutral System Prompt** — The auto-workflow orchestrator call (agent selection phase) now uses a neutral system prompt rather than the user's custom AI persona. Custom personas with strong character instructions were causing structured JSON agent-selection output to fail parsing.
6. **`renderCtxBar` and `buildShareLink` Defined** — Two functions called from UI event handlers (`ctx-modal` Done button and `share-modal` select `onchange`) were never defined in prior versions, causing silent JavaScript errors on every invocation. Both are now implemented.
7. **Dead State Cleanup** — Removed stale module-level variables (`lastAR`, `lastSyn`, `lastCD`) that were written but never read, and a `MAX_CONTEXT_TOKENS` const that was always evaluated before `loadPrefs()` and therefore always stale.

### v1.19 — 2026-03-03

**Reasoning Model / Think Tag Support**

1. **`processThinkTags()` Helper** — New function parses `<think>`, `<reasoning>`, and `<scratchpad>` XML blocks produced by reasoning models (DeepSeek R1, QwQ, Qwen 3, o1-style outputs). Accepts a `context` argument (`'chat'` or `'compose'`) so behaviour can be toggled independently per view.
2. **Live Reasoning Badge — Chat** — While a reasoning model streams its `<think>` block, a pulsing amber **"💭 Thinking…"** badge appears inline in the chat bubble. The dot animates during streaming. Once the model transitions to its actual answer, the badge becomes a collapsible **"💭 Reasoning"** toggle that reveals the full thought process on click without cluttering the main response.
3. **Live Reasoning Badge — Compose** — Identical badge system for the Compose direct-prompt view and workflow synthesis panel. A gold **"💭 Reasoning"** pill appears above the output body; clicking it expands a scrollable pre-formatted reasoning block.
4. **Settings Toggles** — Two independent checkboxes added to Settings → Reasoning / Think Tags: one for Chat and one for Compose. When checked, raw `<think>` blocks are hidden from response text and shown as the collapsible badge. When unchecked, the model's raw reasoning appears inline in the output. Settings persist to `localStorage`.
5. **Streaming-Safe** — The badge state is updated on every streaming chunk, so users see "Thinking…" the moment the reasoning block opens, and the transition to "Reasoning" (collapsed, done) happens the moment the first non-reasoning token arrives — with no layout shift.

### v1.18 — 2026-03-03

**Context Safety, UX Polish & WebGPU Expansion**

1. **Universal Context Budget Guard** — New `safeOutputBudget()` function applied to every `streamAPI` call throughout the app. Computes available output tokens from actual input size rather than percentage guesses: `outputBudget = contextWindow − inputTokens − 256`. Prevents "context size exceeded" errors across all model types — local 8K models, large cloud models (128K+), and WebGPU (4K ctx). Works automatically for any provider without model-specific tuning.
2. **Live Synthesis Streaming** — Final orchestrator synthesis now streams live token-by-token directly into the output panel. Previously used a blocking `callAPIonce` call that would timeout on long reports. Output panel now auto-scrolls into view the moment synthesis begins.
3. **Synthesis UX** — Animated pulsing dots placeholder appears immediately when synthesis starts. Status bar shows a live token counter ("Synthesizing… 312 tokens") updating with each chunk. Spelling corrected: "synthesising" → "synthesizing" throughout.
4. **Image Generation Indicator** — A shimmer placeholder card appears instantly in the output body when AI image generation is triggered, replaced by the actual image on arrival. Previously the output was silent until the image appeared.
5. **Agent Result Dropdowns** — Agent output cards (NEXUS, SCOUT, WEAVE etc.) now render full Markdown in their dropdown panels via `mdToHtml()`. Previously displayed raw plain text.
6. **WebGPU Model Expansion** — Browser WebGPU provider expanded from 8 to 12 models across four VRAM tiers. Each model shows its VRAM requirement and a tier indicator (⚠️ minimum / ✅ recommended / 🔥 enthusiast). New additions: Qwen 2.5 7B ⭐ (recommended), DeepSeek R1 7B (reasoning), Gemma 2 9B, Llama 3.1 70B.
7. **Safari WebGPU Support** — Safari 17+ added to all WebGPU browser requirement strings. WebGPU has been supported in Safari since macOS Sonoma / iOS 17.
8. **Favicon** — App now shows a dark navy tab icon with a gold **N** matching the Nemilia brand palette (`#1a3040` background, `#c9a84c` letterform).
9. **callAPIonce Timeout** — Raised from 90 seconds to 300 seconds. Validation and decomposition calls on large agent outputs with slower local models no longer time out and produce partial JSON.

### v1.11 — 2026-03-02

**UI Polish & Color Refinement**

1. **Gold-Primary Color Scheme** — Light mode accent changed from navy (`#1a3040`) to rich dark gold (`#8b6914`). Primary buttons, active nav indicators, and focus rings now carry Nemilia's gold brand identity consistently. Backgrounds neutralised from warm beige (`#f8f7f4`) to clean gray (`#fafafa`) to eliminate warm/cool temperature clash. Interactive gold (`--amd`) brightened to `#b8941f` for crisper hover borders.
2. **Dark Mode Contrast** — Accent brightened from `#d4b85c` to `#e0c255` for better readability on dark backgrounds. Highlight background (`--alt`) adjusted to `#1c1c12` for improved visibility.
3. **Semantic Color Update** — Green updated to `#16a34a` (warmer, pairs better with gold). Red updated to `#e03131`. All hardcoded `rgba()` values across the stylesheet updated to match new palette.
4. **Spacing & Padding Pass** — Header height increased from 52px to 56px. Button padding increased ~2px throughout. Nav item vertical padding raised from 7px to 9px. Card padding, modal padding, chat message padding, form input padding, and output panel padding all increased for improved breathing room.
5. **Hover Micro-Interactions** — Buttons, cards, pills, and header controls now lift on hover with `translateY(-1px)` or `translateY(-2px)` and escalating box shadows. All transitions unified to `.18s ease` for smoother feel.
6. **Shimmer Loading Animation** — Added `@keyframes shimmer` and `.loading-shimmer` CSS class for skeleton loading states.
7. **Shadow Refinements** — All three shadow tiers (`--s1`, `--s2`, `--s3`) updated with dual-layer definitions for softer, more natural depth.

**Bug Fixes**

8. **Workflow Timer Fix** — Fixed a bug where the elapsed-time timer would continue running (and blink between different numbers) after workflow errors or concurrent runs. Root causes: (a) `timer` was a local variable inside `runWorkflow()` that `stopRun()` couldn't access; (b) no `try/finally` wrapper meant unhandled exceptions leaked the interval; (c) no guard against concurrent runs meant overlapping intervals wrote to the same DOM element. Fix: `runTimer` promoted to module scope, main workflow body wrapped in `try/catch/finally` with guaranteed cleanup, concurrent run guard added at function entry, and `stopRun()` / `openCompose()` now explicitly clear the interval.
9. **Chat Web Search Toggle Fix** — Fixed a bug where the 🔍 Web Search toggle in chat could appear enabled without a fully configured search provider. Added `isSearchConfigured()` helper that checks both provider selection AND API key presence (matching the header pill's existing logic). The toggle chip now only renders when fully configured, auto-resets to OFF when a provider is changed or removed, and the notification message clarifies that both a provider and key are needed. The send function's search guard also uses the same check for consistency.

### v1.10 — 2026-03-01

1. **Enter-to-Send UX** — All four input areas (Compose, Chat, Followup, Direct Followup) now use `Enter` to send and `Shift+Enter` for newlines.
2. **XSS Sanitization** — New `sanitizeVisualHTML()` function strips `<script>` tags, `on*` event handlers, and `javascript:` protocol URLs from all LLM-generated visual outputs.
3. **Context Window Management** — Chat messages and workflow followups now use a sliding window that trims older messages when total character count exceeds `3 × maxTokens × CHARS_PER_TOK`.
4. **Document Auto-Restore** — Raw file blobs are now stored in IndexedDB at upload time. On browser reload, if parsed content is missing, Nemilia automatically re-parses from the stored blob.
5. **Visual Close Buttons** — All rendered visual blocks now have a hover-reveal `✕` button for removal. Removing a visual updates the PDF capture arrays so exports reflect what the user actually wants.
6. **Visual System Cleanup** — Removed unreliable auto-visual triggers. Visual generation is now exclusively user-initiated via the "Generate Visual" button.
7. **O(N) Hybrid Search** — Replaced O(N²) `.find()` inside `.map()` in `hybridSearch()` with pre-computed `Object.fromEntries()` score maps for O(1) lookups.
8. **SLM Punctuation Preservation** — `compressSysPrompt()` now preserves original sentence-ending punctuation when compressing prompts for small local models.
9. **CHARS_PER_TOK Fix** — Fixed an undefined variable reference that crashed the Predictive Execution Engine's `predictRun()` function.
10. **Storage Failure Notifications** — Silent empty `catch{}` blocks on 5 critical storage paths now include `console.warn()` diagnostics and user-facing notifications.
11. **Mobile Input Fix** — Added `font-size: 16px !important` to all inputs in the mobile media query to prevent iOS Safari auto-zoom on focus.

### v1.09 — 2026-02-28

1. **Chat Mode** — A first-class persistent chat interface with streaming, RAG context injection, session memory, conversation history, auto-titling, and `MEMORY[key]: value` extraction.
2. **Auto Workflow (AI Agent Routing)** — A new "🤖 Auto (AI picks agents)" option in the Compose workflow dropdown. The orchestrator selects and orders 1–5 agents automatically.
3. **debugLog fix** — Corrected a recursive call bug in the `debugLog` utility that caused a stack overflow when debug mode was enabled.

### v1.08 — 2026-02-27

1. **Predictive Execution Engine** — Pre-run analysis panel with complexity scoring, ambiguity flags, estimated runtime, and one-click HITL suggestions.
2. **Session Memory Continuity** — Prior session context (workflow, prompt, run digests) auto-injected into the orchestrator on reload.
3. **BSL 1.1 License** — Nemilia transitions from MIT to Business Source License 1.1.

### v1.0 — Initial Release

- 7 specialist agents: SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION
- Human-in-the-Loop: approve, edit, or send feedback at any pipeline stage
- Drag-and-drop workflow builder with live SVG flow preview
- Semantic vector RAG: hybrid Transformers.js embeddings + BM25 keyword search
- WebGPU local inference with visual progress ring and multi-CDN fallback
- 7 image providers: DALL·E 3, FLUX, Stable Diffusion, Aurora, Imagen 4, SD3, Replicate, Fal.ai
- DAG pipeline execution with orchestrator validation and auto-retry
- Document RAG: PDF, DOCX, TXT, MD, CSV with smart chunking
- Persistent memory system with cross-session agent knowledge
- 4 web search providers: Brave, Serper, Tavily, SearXNG
- Collapsible file browser with workspace sync to disk
- AES-256-GCM encrypted key storage with 200K-iteration PBKDF2

---

## License

**Business Source License 1.1 (BSL 1.1)**

Nemilia AI v1.21 is source-available software, free for personal and non-commercial use.

| Parameter | Value |
|---|---|
| Licensed Work | Nemilia AI v1.21 |
| Licensor | Luis Lopez / Nemilia AI |
| Additional Use Grant | Personal use and internal non-commercial evaluation |
| Change Date | 2030-02-27 |
| Change License | MIT License |

On the Change Date, this software automatically converts to the MIT License. Commercial production use prior to the Change Date requires a separate commercial license.

Full BSL 1.1 text: [mariadb.com/bsl11](https://mariadb.com/bsl11/)

---

<div align="center">
  <strong>Nemilia</strong> (neh-MEE-lee-ah) &nbsp;·&nbsp; Nahuatl: <em>to think, to remember, to imagine</em><br/>
  <a href="https://nemilia.com">nemilia.com</a> &nbsp;·&nbsp; <a href="mailto:luis@nemilia.com">luis@nemilia.com</a>
</div>
