# Nemilia AI v1.0

**A browser-native AI workspace with multi-agent orchestration, human-in-the-loop review, semantic vector RAG, and visual workflow design — all in a single HTML file with zero backend.**

*Nemilia (neh-mee-lee-ah) — Nahuatl for "to think, to remember, to imagine"*

---

## Table of Contents

- [What Is Nemilia?](#what-is-nemilia)
- [Why It Exists](#why-it-exists)
- [Core Concepts](#core-concepts)
- [Feature Overview](#feature-overview)
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
  - [Image Generation with VISION](#tutorial-image-generation-with-vision)
  - [Running Local Models (WebGPU)](#tutorial-running-local-models-webgpu)
  - [Workspace & File Management](#tutorial-workspace--file-management)
  - [Prompt Templates](#tutorial-prompt-templates)
  - [Memory System](#tutorial-memory-system)
- [Execution Flow](#execution-flow)
- [Browser Compatibility](#browser-compatibility)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Changelog](#changelog)
- [License](#license)

---

## What Is Nemilia?

Nemilia AI is an entirely client-side AI platform packed into a single, self-contained HTML file. There is no server, no installer, no account to create, and no database to configure. You open one file in a browser and get a full multi-agent AI workspace.

At its core, Nemilia lets you define **specialist AI agents** — each with a distinct role, personality, and system prompt — then wire them into **pipelines called workflows**. When you run a workflow, Nemilia orchestrates the agents in dependency order: a research agent gathers information, an analyst extracts insights, a writer produces content, a reviewer critiques it, and a synthesiser merges everything into a polished final report. Each agent's output is scored for quality and automatically retried if it falls short.

This is not a chatbot. It is a structured AI workspace where multiple models collaborate on complex tasks with human oversight at every stage.

### What Can You Do With It?

- **Research reports** — SCOUT researches a topic, LENS analyses findings, QUILL writes the report, FORGE reviews it, WEAVE produces the executive summary. Five agents, one click.
- **Document Q&A** — upload a 200-page PDF, ask questions, and get answers grounded in specific passages with hybrid semantic + keyword search.
- **Live web research** — NEXUS searches the internet in real-time, then downstream agents process and synthesise the results with source citations.
- **Visual content** — VISION generates Chart.js charts, SVG diagrams, HTML infographics, and (optionally) AI-generated images from DALL·E, FLUX, or Stable Diffusion.
- **Offline AI** — run Llama, Phi, Qwen, or Gemma directly in your browser via WebGPU. No API key, no server, no internet after the initial model download.
- **Review and steer** — pause the pipeline at any agent with human-in-the-loop checkpoints. Approve the output, edit it inline, or send feedback to re-run that step.

### What Makes This Different?

| Feature | Nemilia | Typical AI Chat | AI Platform (Langchain, etc.) |
|---------|---------|-----------------|-------------------------------|
| Setup | Open an HTML file | Create account | Install Python, Docker, etc. |
| Multi-agent | Built-in orchestrator | Single model | Requires custom code |
| Human review | One-click HITL | None | Custom implementation |
| Data privacy | 100% client-side | Data on their servers | Varies |
| Document search | Hybrid vector + BM25 | Upload & hope | Vector DB setup |
| Provider lock-in | 13 providers, swap anytime | Locked to one | Configurable but complex |
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

### Agents & Orchestration
- 7 built-in specialist agents (SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION)
- Custom agent creation with role prompts, icons, colours, and per-agent model overrides
- DAG-staged parallel execution with rate-limit awareness
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

### Image & Visual Generation
- VISION generates Chart.js configs, SVG diagrams, and HTML infographics (no API needed)
- Optional AI image providers: DALL·E 3, FLUX, Stable Diffusion, Recraft V3
- Auto-prompting: orchestrator extracts `IMAGE_PROMPT:` directives from agent outputs

### Browser-Native AI (WebGPU)
- Run Llama, Phi, Qwen, Gemma, Mistral models entirely in the browser
- Powered by MLC WebLLM with GPU acceleration
- Models download once (~1–5GB) and cache in the browser for instant future loads
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

## Architecture

### Single-File Design

The entire application — HTML structure, CSS styling, JavaScript logic, and embedded SVG/base64 assets — lives in one `.html` file (~4,500 lines). There is no build step, no bundler, no transpiler, and no framework dependency. You can read every line of code by opening the file in a text editor.

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
│                          │                           │                   │
│                          ▼                           ▼                   │
│                   ┌──────────────────────────────────────┐               │
│                   │           Final Synthesis             │               │
│                   │    Markdown + Charts + Images + PDF   │               │
│                   └──────────────────────────────────────┘               │
│                                                                         │
│  ┌────────────────────────────────────────────────────────────────────┐  │
│  │                        STORAGE LAYER                               │  │
│  │                                                                    │  │
│  │  Tier 1: File System Access API (Chrome/Edge)                     │  │
│  │    └─ Plain files on disk: JSON agents, Markdown prompts          │  │
│  │    └─ Editable in VS Code, Git-versionable                        │  │
│  │    └─ Non-destructive: never overwrites existing files            │  │
│  │                                                                    │  │
│  │  Tier 2: IndexedDB                                                │  │
│  │    └─ Documents, vector embeddings (384 × N float arrays)        │  │
│  │    └─ Encrypted API keys, run results, large content              │  │
│  │    └─ No practical size limit, persists across sessions           │  │
│  │                                                                    │  │
│  │  Tier 3: localStorage (fallback)                                  │  │
│  │    └─ Settings, workspace metadata, agent configs                 │  │
│  │    └─ ~5MB limit, used when IndexedDB unavailable                 │  │
│  └────────────────────────────────────────────────────────────────────┘  │
│                                                                         │
│  ┌────────────────────────────────────────────────────────────────────┐  │
│  │                      EXTERNAL APIs (your choice)                   │  │
│  │                                                                    │  │
│  │  LLM: Groq / OpenAI / Anthropic / Gemini / Kimi / DeepSeek / ... │  │
│  │  Search: Brave / Serper / Tavily / SearXNG                        │  │
│  │  Images: DALL·E / FLUX / Stable Diffusion / Recraft               │  │
│  │  Local: Ollama / LM Studio / Jan / Llamafile / WebGPU (browser)   │  │
│  └────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```

### RAG Pipeline Architecture

```
Document Upload
    │
    ▼
┌───────────────┐     ┌──────────────────────────┐
│  Parser        │────▶│  Chunker                  │
│  PDF.js / DOCX │     │  Paragraph-level split    │
│  / TXT / CSV   │     │  ~500–1000 chars/chunk    │
└───────────────┘     └────────────┬─────────────┘
                                   │
                    ┌──────────────┼──────────────┐
                    ▼              ▼              ▼
             ┌──────────┐  ┌──────────┐  ┌──────────┐
             │ Chunk 1   │  │ Chunk 2   │  │ Chunk N   │
             └─────┬─────┘  └─────┬─────┘  └─────┬─────┘
                   │               │              │
                   ▼               ▼              ▼
            ┌────────────────────────────────────────────┐
            │  Transformers.js  ·  all-MiniLM-L6-v2      │
            │  384-dimensional embeddings                 │
            │  ~5ms/chunk (GPU) · ~30ms/chunk (CPU)       │
            └──────────────────┬─────────────────────────┘
                               │
                               ▼
                     ┌──────────────────┐
                     │  IndexedDB        │
                     │  Float32 arrays   │
                     │  Persist forever  │
                     └──────────────────┘

User Query
    │
    ├──▶ Cosine similarity search ──────▶ 60% weight ──┐
    │    (understands meaning)                          │
    │                                                    ├──▶ Hybrid-ranked
    └──▶ BM25 keyword search ───────────▶ 40% weight ──┘    top-K chunks
         (matches exact terms)                                    │
                                                                  ▼
                                                        Injected into
                                                        agent context
                                                        (12K char budget)
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

API keys are the most sensitive data Nemilia handles. They are protected with multiple layers:

**Encryption at rest** — every API key is encrypted with **AES-256-GCM** before storage. The encryption key is derived via **PBKDF2 with 200,000 iterations** of SHA-256 using a provider-specific salt. This makes brute-force extraction computationally expensive even if someone gains access to your browser's storage.

**Storage isolation** — encrypted key blobs are stored in IndexedDB (primary) with localStorage fallback. Keys are **never written to disk as plaintext**, even when using the File System API workspace sync. The workspace folder contains agents, prompts, and workflows — never keys.

**Transmission scope** — a key is decrypted only at the moment of an API call and sent exclusively to the endpoint URL hard-coded for that provider (`api.groq.com` for Groq, `api.openai.com` for OpenAI, etc.). Keys are never sent to any Nemilia server (there is none), analytics service, or third-party endpoint.

**No cross-provider leakage** — each provider's key is stored and encrypted independently. Configuring OpenAI does not expose your key to Groq's endpoint or vice versa.

### Data Privacy

**Zero telemetry** — Nemilia contains no analytics scripts, no tracking pixels, no beacons, and no phone-home code of any kind. You can verify this by reading the source — it's a single file.

**Client-side processing** — all computation happens in your browser's JavaScript runtime:
- Document parsing, chunking, and embedding → local
- BM25 scoring and vector search → local
- Memory management → local
- Workflow orchestration and agent prompt construction → local
- Markdown rendering, chart generation, PDF export → local

**What leaves your browser** (and only when you initiate it):
- **LLM API calls** — your prompts and agent system prompts are sent to whichever provider you configure, using their standard API over HTTPS.
- **Search API calls** — when NEXUS runs, search queries go to the search provider you configured (Brave, Serper, Tavily, or your SearXNG instance).
- **Image API calls** — when VISION generates AI images, prompts go to the configured image provider.
- **CDN library loads** — PDF.js, WebLLM, Transformers.js, and Chart.js are fetched from public CDNs when their features are first used.

**Nothing else leaves your browser.** There is no server, no account, no telemetry endpoint.

### Content Security

- **XSS prevention** — all user-facing content is sanitised through the `esc()` function before DOM insertion. Agent outputs are rendered as Markdown, never as raw HTML injection.
- **CSP meta tag** — Content Security Policy restricts script sources.
- **Style injection prevention** — colour values from user input are sanitised to prevent CSS injection attacks.
- **Non-destructive workspace** — when re-seeding a workspace folder, Nemilia checks each file before writing. Existing files are never overwritten or deleted. This prevents data loss on page reload.

### WebGPU / Local Model Privacy

When using the WebGPU provider, **absolutely nothing leaves your browser** after the initial model download. The model weights are cached in the browser's storage, and all inference runs on your local GPU. This is true offline AI — no API calls, no server, no internet required after the first download.

---

## Provider Reference

| Provider | Free Tier | Recommended Model | Setup Link |
|----------|-----------|-------------------|------------|
| **Groq** | Yes (generous) | Llama 3.3 70B | [console.groq.com](https://console.groq.com) |
| **OpenRouter** | Yes (limited) | DeepSeek V3 | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **Google Gemini** | Yes | Gemini 2.5 Flash | [aistudio.google.com](https://aistudio.google.com/apikey) |
| **Anthropic** | No | Claude Sonnet 4 | [console.anthropic.com](https://console.anthropic.com) |
| **OpenAI** | No | GPT-4.1 | [platform.openai.com](https://platform.openai.com) |
| **Mistral** | No | Mistral Large | [console.mistral.ai](https://console.mistral.ai) |
| **DeepSeek** | Yes | DeepSeek V3 | [platform.deepseek.com](https://platform.deepseek.com) |
| **Kimi (Moonshot)** | $5 bonus | Kimi K2 / K2.5 | [platform.moonshot.ai](https://platform.moonshot.ai) |
| **xAI** | No | Grok 3 | [console.x.ai](https://console.x.ai) |
| **Ollama** | Local | Any | [ollama.com](https://ollama.com) |
| **LM Studio** | Local | Any | [lmstudio.ai](https://lmstudio.ai) |
| **Jan** | Local | Any | [jan.ai](https://jan.ai) |
| **WebGPU** | Local | Llama 3.2 3B | Built-in (Chrome 121+) |

---

## Quick Start

1. Open `Nemilia.html` in Chrome, Edge, or any modern browser.
2. Click **🚀 Set Up Your AI Provider** in the header.
3. Pick a provider (Groq is free), paste your API key, select a model, click **Save**.
4. Go to **Compose**, type a prompt, and press **Ctrl+Enter** or click **Run**.

That's it. Everything saves automatically in your browser.

---

## Tutorial: Connecting an AI Provider

Nemilia needs an LLM to power its agents. You have three options: cloud API (fastest setup), local server (Ollama/LM Studio), or in-browser (WebGPU, no account needed).

### Cloud API (recommended for beginners)

1. **Click the gold pill** in the header that says "🚀 Set Up Your AI Provider".
2. The provider modal opens showing a grid of providers. **Click Groq** (it's free with generous limits).
3. If you don't have a Groq account, click the blue link to [console.groq.com](https://console.groq.com). Create an account and generate an API key.
4. **Paste your API key** in the input field and click **Save key**.
5. **Select a model** — "Llama 3.3 70B" is the best free option.
6. Click **Save** at the bottom. The header pill turns green and shows your provider name.

**Tip:** Your API key is encrypted with AES-256-GCM before storage. It never leaves your browser except when sent to the provider's API endpoint.

### Switching providers later

Click the provider pill in the header anytime. Your keys for all providers are remembered — you can switch instantly.

---

## Tutorial: Your First Workflow Run

Workflows chain multiple specialist agents together. Nemilia ships with two built-in workflows.

### Step by step

1. Navigate to **Compose** (left sidebar, top item).
2. In the toolbar above the text area, find the **workflow dropdown** (it says "Direct prompt" by default). Click it and select **"Research Suite"**.
3. Type a research topic in the text area. For example:
   ```
   Analyse the current state of fusion energy research.
   Key players, recent breakthroughs, and timeline to commercial viability.
   ```
4. Press **Ctrl+Enter** (or ⌘+Enter on Mac) or click the **Run** button.
5. Watch the pipeline execute:
   - **SCOUT** researches the topic
   - **LENS** analyses the findings
   - **QUILL** writes the content
   - **FORGE** reviews for quality
   - **WEAVE** synthesises everything into a final report
6. Each agent's output appears in a card with a quality score (1–10). The final synthesis appears at the bottom.
7. Click **📄 PDF** to download the report, or copy the output directly.

### What happens behind the scenes

The orchestrator decomposes your prompt into sub-tasks, one per agent. Agents run in DAG-staged order (search first, then analysis in parallel, then synthesis). Each output is validated — if an agent scores below 6, it automatically retries up to twice.

---

## Tutorial: Creating Custom Agents

The built-in agents cover common needs, but you can create specialists for your domain.

### Creating an agent

1. Go to **Agents** in the left sidebar.
2. Click **+ New agent**.
3. Fill in the fields:
   - **Name**: Short uppercase name (e.g. "LEGAL")
   - **Role**: One-line description (e.g. "Contract analysis & compliance review")
   - **Icon**: Pick an emoji (e.g. ⚖️)
   - **Colour**: Choose a brand colour for the agent's card
   - **System prompt**: The most important field. Write detailed instructions for what the agent should do, what format to use, and what to include. Be specific.
   - **Model override** (optional): Force this agent to use a specific model regardless of the default.
   - **Requires human approval (HITL)**: Check this to pause the pipeline for review after this agent runs.
4. Click **Save agent**.

### Example system prompt for a "LEGAL" agent

```
You are a legal analysis specialist. Review content for:
- Contractual obligations and liabilities
- Regulatory compliance issues
- Risk exposure and mitigation strategies
- Ambiguous or problematic language

Flag items as HIGH / MEDIUM / LOW risk. For each risk, provide:
1. The specific clause or issue
2. Why it matters
3. Recommended action

Tone: precise, professional, cautious.
```

After saving, add the agent to any workflow via the workflow builder.

---

## Tutorial: Building Workflows with Drag-and-Drop

Workflows define which agents run and in what order. The visual builder lets you design pipelines by dragging agents around.

### Creating a new workflow

1. Go to **Workflows** in the left sidebar.
2. Click **+ New workflow**.
3. **Name** your workflow (e.g. "Legal Review Pipeline").
4. Write a **default prompt template** — this pre-fills when someone selects the workflow. Use `{{placeholders}}` for variable parts:
   ```
   Review the following contract: {{contract_text}}
   Focus on: {{areas_of_concern}}
   ```
5. In the **Agents** section, use the dropdown to add agents. Each appears as a draggable card.

### Reordering agents

- **Grab the ⠿ handle** on any agent card and **drag it** up or down to reorder.
- The **SVG flow preview** at the bottom updates in real-time as you reorder.
- The order matters: agents at the top run first, and their outputs feed into agents below them.

### Adding HITL checkpoints

- Click the **⏸ HITL** button on any agent card to toggle a human-review checkpoint.
- When enabled, the button turns amber and a "⏸ human review" divider appears in the flow preview.
- HITL overrides in the workflow are independent of the agent's global HITL setting.

### Workflow settings

Toggle these options as needed:
- **Orchestrator validation**: scores each agent's output and retries if quality is low
- **DAG execution**: runs agents in dependency-ordered stages (faster than sequential)
- **Memory injection**: includes saved memories in agent context
- **SLM mode**: compresses prompts for small models (WebGPU)

Click **Save workflow**. It appears in the Compose dropdown ready to use.

---

## Tutorial: Human-in-the-Loop (HITL) Review

HITL lets you pause the pipeline at any agent to review, edit, or redirect the output before it continues.

### Enabling HITL

There are two ways:
- **Per agent (global)**: Edit an agent → check "⏸ Requires human approval (HITL)". This applies everywhere the agent is used.
- **Per workflow (override)**: In the workflow builder, click the ⏸ button on a specific agent card. This only applies within that workflow.

### What happens during a run

1. The pipeline runs normally until it reaches an HITL-flagged agent.
2. That agent completes its work, then **the pipeline pauses**.
3. The agent's card pulses amber and shows a **review panel** with three action buttons.

### The three actions

**✓ Approve** — You're satisfied with the output. Click to continue the pipeline as-is.

**✏️ Edit** — Click to reveal an editable text area with the full output. Make your changes (fix facts, adjust tone, add detail), then click **✏️ Save edit**. The pipeline continues with your modified version.

**💬 Send Feedback** — Click to reveal a feedback input. Type what's wrong or what you want changed (e.g. "Too technical — simplify for a general audience"). Click **💬 Re-run with feedback**. The agent re-runs with your feedback injected into its prompt, then pauses again for another review. You can loop this as many times as needed.

### Example use case

Research Suite workflow: SCOUT → LENS → QUILL → WEAVE. You enable HITL on LENS.

1. SCOUT completes research automatically.
2. LENS completes analysis — pipeline pauses.
3. You review and notice LENS missed a key competitor. You click **💬 Send Feedback**: "Include analysis of Company X's recent patent filing."
4. LENS re-runs with your feedback, pauses again.
5. Analysis is now complete. You click **✓ Approve**.
6. QUILL and WEAVE run automatically with the improved analysis.

---

## Tutorial: Document RAG (Upload & Search)

RAG (Retrieval-Augmented Generation) lets agents reference your uploaded documents when answering questions.

### Uploading documents

1. Go to **Documents** in the left sidebar.
2. **Drag and drop** files into the drop zone, or click to browse. Supported formats: PDF, DOCX, TXT, MD, CSV.
3. Nemilia parses the document, splits it into chunks, and starts generating vector embeddings automatically.
4. A progress bar shows embedding status. When complete, a green **🧠 Vector** badge appears.

### How search works

Nemilia uses **hybrid search** combining two techniques:
- **Vector search** (60% weight): Understands meaning. "What are the financial risks?" finds paragraphs about "monetary exposure" even though the exact words don't match.
- **BM25 keyword search** (40% weight): Matches exact terms. Ensures you find "Section 4.2" when you search for it.

### Using documents in a workflow

1. In **Compose**, click **📎 Context** in the toolbar.
2. Select which documents to include. A chip appears showing active documents.
3. Run your prompt. The most relevant chunks are automatically injected into each agent's context (up to 12,000 characters, distributed proportionally across documents).

### Performance notes

- Embedding uses `all-MiniLM-L6-v2` (22MB model, downloaded once and cached).
- Speed: ~5ms per chunk on GPU, ~30ms on CPU.
- A 50-page PDF (~200 chunks) takes 1–6 seconds to embed.
- Embeddings persist in IndexedDB — they survive page refreshes.

---

## Tutorial: Web Search with NEXUS

NEXUS is a special agent that can search the live web during workflow execution.

### Setting up web search

1. Go to **Connections** in the left sidebar.
2. Under **Search Provider**, choose one:
   - **Brave Search** — free tier at [brave.com/search/api](https://brave.com/search/api/)
   - **Serper** (Google results) — free tier at [serper.dev](https://serper.dev/)
   - **Tavily AI** — free tier at [tavily.com](https://tavily.com/)
   - **SearXNG** — self-hosted, no API key needed (enter your instance URL)
3. Paste your API key and click **Save**.

### Using NEXUS

NEXUS is included in the "Web Research Suite" workflow by default. When a workflow runs with NEXUS:
1. NEXUS runs first (Stage 1 in DAG mode).
2. It generates search queries, retrieves results, and summarises findings with inline `[Title](URL)` citations.
3. Its output is passed to all downstream agents as additional context.

You can also add NEXUS to any custom workflow.

---

## Tutorial: Image Generation with VISION

VISION creates charts, diagrams, and optionally AI-generated images.

### Code-based visuals (no API key needed)

VISION generates visual content as code that Nemilia renders in the browser:
- **Charts**: Chart.js configs (bar, line, pie, radar, doughnut, polarArea)
- **SVG diagrams**: process flows, architecture diagrams, comparisons
- **HTML infographics**: styled cards, dashboards, comparison tables

These work with any text provider — no image API required.

### AI-generated images (optional)

For photographic images, illustrations, and art:
1. Go to **Settings** → scroll to **Image Generation**.
2. Choose a provider: DALL·E 3 (OpenAI), FLUX (Together AI), Stable Diffusion (Stability AI), or Recraft V3 (Replicate).
3. Paste the API key and click **Save**.

When VISION detects a visual request, it generates both code-based visuals AND an AI image if a provider is configured.

---

## Tutorial: Running Local Models (WebGPU)

Run AI models entirely in your browser — no API key, no server, no internet after the first download.

### Requirements

- **Chrome 121+** or **Edge 121+** (WebGPU must be available)
- A GPU (integrated or dedicated)
- 2–8 GB of free memory depending on model size

### Setup

1. Click the provider pill → select **Browser (WebGPU)**.
2. **Choose a model** from the dropdown:
   - **Llama 3.2 1B** (~0.8GB) — fastest, good for simple tasks
   - **Llama 3.2 3B** (~1.8GB) — best balance of speed and quality
   - **Phi 3.5 Mini** (~2.4GB) — strong reasoning
   - **Llama 3.1 8B** (~4.5GB) — best quality, needs more memory
3. Click **⬇ Download & Load Model**.
4. The **circular progress ring** shows download percentage. A linear progress bar and status text update in real-time as the model downloads (~1–5GB). **This is a one-time download** — the model is cached in your browser for future use.
5. Once loaded, the ring shows ✓ green and the header pill turns green. Run workflows offline.

### Troubleshooting

If you see "Could not load WebLLM library":
- **Check internet** — the first step downloads the WebLLM engine from a CDN (~200KB). Nemilia tries 4 different CDNs automatically (esm.run, jsdelivr, esm.sh).
- **Disable ad blockers** — browser extensions that block third-party scripts can prevent CDN imports.
- **Try Chrome/Edge** — Firefox has limited WebGPU support. Safari doesn't support it yet.
- **Check GPU** — go to `chrome://gpu` and verify "WebGPU" shows as "Hardware accelerated".
- **Corporate networks** — firewalls may block CDN domains. Try a different network.

### Important notes

- WebGPU models are **not local files** — they download from CDN servers on first use, then cache permanently.
- Enable **SLM mode** in workflow settings to compress prompts for better small-model performance.
- Quality is lower than cloud models (3B params vs 70B+), but it's completely private and free.

---

## Tutorial: Workspace & File Management

Nemilia can sync your workspace to a folder on disk, giving you real files alongside the in-browser experience.

### Setting up a workspace folder (Chrome/Edge)

1. Click the **folder icon** in the header or **Open workspace** in the sidebar footer.
2. The setup wizard appears. Click **Choose folder** and select or create a directory.
3. Click **Next** — Nemilia creates folders and writes default agent/prompt/workflow files.
4. **If the folder already has files from a previous session, nothing is overwritten.** Nemilia only creates missing files and preserves everything else.

### The Files panel

Once connected, a **Files** section appears in the sidebar below Results:
- **Click "▶ Files"** to expand/collapse the entire file tree.
- **Click any 📁 folder** (agents, prompts, workflows, docs, results) to expand/collapse just that folder.
- **Click any file** to open it in the built-in text editor.
- Click **+** to create a new file.

### Editing files

Files open in a simple editor. Make changes and click **Save**. The file writes to both disk (if connected) and IndexedDB.

Since files are plain JSON and Markdown, you can also edit them in VS Code, Notepad, or any editor. Changes sync when you reload Nemilia.

### Storage badge

The header badge shows your active mode: **FS** (filesystem on disk), **IDB** (IndexedDB), or **LS** (localStorage fallback).

---

## Tutorial: Prompt Templates

Save reusable prompts with variable placeholders for repetitive tasks.

### Creating a template

1. Go to **Prompts** in the left sidebar.
2. Click **+ New prompt**.
3. Fill in name, description, tags, and content. Use `{{double_braces}}` for variables:
   ```
   Generate a weekly status report for {{team_name}}.
   Key accomplishments: {{accomplishments}}
   Blockers: {{blockers}}
   Format as a professional email to {{audience}}.
   ```
4. Click **Save prompt**.

### Using a template

In Compose, click a prompt chip below the toolbar. The template fills in with placeholders highlighted. Replace them with your content, then run.

---

## Tutorial: Memory System

Agents can save facts between runs, building institutional knowledge over time.

### How it works

Any agent can write `MEMORY[key]: value` in its output:
```
MEMORY[company_founding]: Acme Corp was founded in 2019 by Jane Smith.
MEMORY[main_competitor]: Their primary competitor is GlobalTech Inc.
```

These are automatically extracted and stored. On future runs with memory enabled, all stored memories are injected into every agent's context.

### Managing memories

Go to **Memory** in the left sidebar. You can view, edit, and delete any stored key-value pair. Use descriptive keys (`quarterly_revenue_2024` not just `revenue`) for clarity.

---

## Execution Flow

```
User Prompt
    │
    ▼
┌─────────────┐
│ ORCHESTRATOR │  ← Decomposes prompt into agent subtasks
└──────┬──────┘
       │
       ▼
┌──────────────┐
│   NEXUS      │  ← Web search (Stage 1, if included)
│  🌐 Stage 1  │
└──────┬───────┘
       │  ⏸ HITL checkpoint (if enabled)
       ▼
┌──────────────────────────────────┐
│  SCOUT  │  LENS  │  QUILL       │  ← Analysis (Stage 2, parallel)
│       🔍📊✍️                     │
└──────────┬───────────────────────┘
           │  ⏸ HITL checkpoint (if enabled)
           ▼
┌──────────────┐
│    WEAVE     │  ← Synthesis (Stage 3)
│  ⚡ Stage 3   │
└──────┬───────┘
       ▼
┌──────────────┐
│   VISION     │  ← Charts, diagrams, images (Stage 4)
│  🎨 Stage 4  │
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
| WebGPU (local LLM) | ✅ | ✅ | ⚠️ limited | ❌ |
| Vector RAG embeddings | ✅ | ✅ | ✅ | ✅ |
| PDF parsing | ✅ | ✅ | ✅ | ✅ |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/⌘ + Enter` | Run prompt |
| `Ctrl/⌘ + K` | Focus compose input |

---

## Changelog

### v1.0 — Initial Release

- 7 specialist agents: SCOUT, LENS, QUILL, FORGE, WEAVE, NEXUS, VISION
- Human-in-the-Loop: approve, edit, or send feedback at any pipeline stage
- Drag-and-drop workflow builder with live SVG flow preview
- Semantic vector RAG: hybrid Transformers.js embeddings + BM25 keyword search
- 13 LLM providers: Groq, OpenRouter, Gemini, OpenAI, Anthropic, Mistral, DeepSeek, Kimi (Moonshot), xAI, Ollama, LM Studio, Jan, Llamafile
- WebGPU local inference with visual progress ring and multi-CDN fallback
- 5 image providers: DALL·E, FLUX, Stable Diffusion, Recraft, Replicate
- DAG pipeline execution with orchestrator validation and auto-retry
- Document RAG: PDF, DOCX, TXT, MD, CSV with smart chunking
- Persistent memory system with cross-session agent knowledge
- 4 web search providers: Brave, Serper, Tavily, SearXNG
- Collapsible file browser with workspace sync to disk
- Non-destructive saves: existing files never overwritten on reload
- AES-256-GCM encrypted key storage with 200K-iteration PBKDF2
- Navy/gold visual design with dark theme

---

## License

MIT — free to use, modify, and distribute.

---

*Built with care. No frameworks were harmed in the making of this application.*
