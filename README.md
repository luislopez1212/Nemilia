<div align="center">
<img src="full_logo.png" alt="Nemilia AI Workspace" width="340" />

  <h1>Nemilia — AI OS for the Browser · v2.1</h1>

  <p><strong>One file. Any model. No server.</strong></p>

  <p>
    Multi-agent orchestration &nbsp;·&nbsp; Chrome extension capture &nbsp;·&nbsp; Document RAG &nbsp;·&nbsp; Live web research<br/>
    Offline local models &nbsp;·&nbsp; Zero backend &nbsp;·&nbsp; Zero install &nbsp;·&nbsp; 100% client-side
  </p>

  <p>
    <a href="https://nemilia.com">nemilia.com</a> &nbsp;·&nbsp;
    <a href="https://nemilia.com/demo">Demo Videos</a> &nbsp;·&nbsp;
    <a href="mailto:luis@nemilia.com">luis@nemilia.com</a>
  </p>

  <img src="https://img.shields.io/badge/version-2.1-gold" alt="version" />
  <img src="https://img.shields.io/badge/license-BSL_1.1-orange" alt="license" />
  <img src="https://img.shields.io/badge/backend-none-brightgreen" alt="no backend" />
  <img src="https://img.shields.io/badge/install-open%20HTML%20file-brightgreen" alt="install" />

</div>

---

Nemilia turns any browser into a complete AI production environment. Capture content from the web with the Chrome extension, route it through multi-agent workflows, search your document library, and deliver finished results — all inside a single `~730KB` HTML file with no server, no install, and no data leaving your machine.

*Nemilia (neh-mee-lee-ah) — Nahuatl for "to think, to remember, to imagine"*



***NOTE 3/24/26 - Chrome Extension — now available on the Chrome Web Store → https://chromewebstore.google.com/detail/inkhagbajnhcnedmjhppgloeamfmhkfl
Will be adding link in app with next release.

---

## Demo Videos

[![Nemilia v2.1 — App Tour & Workflow Run](https://nemilia.com/screenshots/compose.png)](https://nemilia.com/videos/Nemilia_Intro.mp4)
**Part 1 — App Tour & Workflow Run** · 1:52 · Nav overview, Chrome extension capture, Captures inbox, multi-agent pipeline executing live

[![Nemilia v2.1 — Results, Agents & Workflows](https://nemilia.com/screenshots/results.png)](https://nemilia.com/videos/Nemilia_Outro.mp4)
**Part 2 — Results, Agents & Workflows** · 2:40 · Workflow Results, agent editor, workflow builder, Build section walkthrough

▶️ [Watch both at nemilia.com/demo](https://nemilia.com/demo)

---

## Table of Contents

- [What Is Nemilia?](#what-is-nemilia)
- [Quick Start](#quick-start)
- [Screenshots](#screenshots)
- [The v2.1 Pipeline](#the-v21-pipeline)
- [Core Concepts](#core-concepts)
- [Feature Overview](#feature-overview)
  - [Chrome Extension](#chrome-extension)
  - [Captures Inbox](#captures-inbox)
  - [Chat Mode](#chat-mode)
  - [Compose & Workflow Mode](#compose--workflow-mode)
  - [Multi-Agent DAG Orchestration](#multi-agent-dag-orchestration)
  - [Human-in-the-Loop (HITL)](#human-in-the-loop-hitl)
  - [Workflow Builder](#workflow-builder)
  - [Library & Document RAG](#library--document-rag)
  - [Web Search](#web-search)
  - [Image & Visual Generation](#image--visual-generation)
  - [Browser-Native AI (WebLLM)](#browser-native-ai-webllm)
  - [Memories](#memories)
  - [Workflow Results](#workflow-results)
  - [Workspace & Storage](#workspace--storage)
- [Tutorials](#tutorials)
  - [Installing the Chrome Extension](#tutorial-installing-the-chrome-extension)
  - [Capturing with the Extension](#tutorial-capturing-with-the-extension)
  - [Triaging Captures](#tutorial-triaging-captures)
  - [Connecting an AI Provider](#tutorial-connecting-an-ai-provider)
  - [Your First Workflow Run](#tutorial-your-first-workflow-run)
  - [Creating Custom Agents](#tutorial-creating-custom-agents)
  - [Building Custom Workflows](#tutorial-building-custom-workflows)
  - [Human-in-the-Loop Review](#tutorial-human-in-the-loop-review)
  - [Library & Document RAG](#tutorial-library--document-rag)
  - [Web Search with NEXUS](#tutorial-web-search-with-nexus)
  - [Per-Agent Web Search](#tutorial-per-agent-web-search)
  - [Running Local Models (WebLLM)](#tutorial-running-local-models-webllm)
  - [Connecting a Custom API Provider](#tutorial-connecting-a-custom-api-provider)
  - [Memory System](#tutorial-memory-system)
  - [Prompt Templates](#tutorial-prompt-templates)
  - [Workspace & File Management](#tutorial-workspace--file-management)
  - [MCP Tool Execution](#tutorial-mcp-tool-execution)
- [Provider Reference](#provider-reference)
- [Architecture](#architecture)
- [Security & Privacy](#security--privacy)
- [Browser Compatibility](#browser-compatibility)
- [Settings Reference](#settings-reference)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [What's New in v2.1](#whats-new-in-v21)
- [License](#license)

---

## What Is Nemilia?

Nemilia is an entirely client-side AI platform in a single self-contained HTML file. No server, no installer, no account, no database. Open one file in a browser and get a full multi-agent AI workspace.

The Chrome extension captures pages, selections, screenshots, and images directly into a **Captures inbox**. From there, items can be triaged to Compose, Chat, a Workflow, or promoted to the **Library** for RAG. Agents run in parallel DAG-staged pipelines, score each other's work, retry automatically, and deliver finished output to **Workflow Results** — ready to export as Word, PDF, Markdown, or plain text.

### What Makes This Different?

| Feature | Nemilia | Typical AI Chat | AI Platform (LangChain, etc.) |
|---------|---------|-----------------|-------------------------------|
| Setup | Open an HTML file | Create account | Install Python, Docker, etc. |
| Capture | Chrome extension → Captures inbox | Paste manually | Custom code |
| Multi-agent | Built-in orchestrator + auto-routing | Single model | Custom code |
| Human review | Per-agent HITL with audio alert | None | Custom implementation |
| Data privacy | 100% client-side | Data on their servers | Varies |
| Document search | Hybrid vector + BM25 | Upload & hope | Vector DB setup |
| Provider lock-in | Any provider, swap anytime | Locked to one | Configurable but complex |
| Offline mode | WebLLM in-browser | No | No |
| Cost tracking | Real-time per-token est. cost | Post-hoc (maybe) | Custom logging |

---

## Quick Start

1. Download `Nemilia_v2_1.html` from [GitHub Releases](https://github.com/luislopez1212/Nemilia)
2. Open in Chrome 121+, Edge 121+, Safari 17+, or Firefox 120+
3. Click **🚀 Set Up Your AI Provider** in the header and connect a provider
4. Go to **Create → Compose**, pick a workflow, write a prompt, press `Ctrl+Enter`

The setup wizard appears only once — every subsequent open goes straight to your workspace.

**Optional:** Install the Chrome extension for web capture ([tutorial below](#tutorial-installing-the-chrome-extension)).

> **Note:** The Chrome extension is currently pending Chrome Web Store review. Until approved, install manually using the steps in the tutorial. The developer mode banner Chrome displays is expected and safe.

---

## Screenshots

<div align="center">
  <img src="https://nemilia.com/screenshots/compose.png" alt="Nemilia Compose — workflow selected, article attached, Pre-Run Analysis" width="98%" />
</div>

<div align="center">
  <img src="https://nemilia.com/screenshots/extension-contextmenu.png" alt="Chrome extension right-click — capture page or run workflow" width="49%" />
  <img src="https://nemilia.com/screenshots/captures.png" alt="Captures inbox — tagged, searched, triage actions" width="49%" />
</div>

<div align="center">
  <img src="https://nemilia.com/screenshots/workflow-running.png" alt="Multi-agent workflow executing — agents streaming in parallel" width="49%" />
  <img src="https://nemilia.com/screenshots/results.png" alt="Workflow Results — finished synthesis with export options" width="49%" />
</div>

<div align="center">
  <img src="https://nemilia.com/screenshots/AI_Providers.png" alt="AI provider configuration — full provider grid" width="98%" />
</div>

---

## The v2.1 Pipeline

```
Browser page / article / image
  └─▶ Chrome Extension (right-click capture or popup)
        └─▶ Captures Inbox — vision analysis, auto-tagging, BM25 + vector embedding
              └─▶ Triage → Compose / Chat / Workflow / Library
                    └─▶ Multi-agent DAG pipeline
                          └─▶ Orchestrator decomposition → per-agent briefings
                                └─▶ Stage 1 — NEXUS (web search, if in workflow)
                                      └─▶ Stage 2 — SCOUT, LENS, QUILL (parallel)
                                            └─▶ Stage 3 — FORGE (review)
                                                  └─▶ Stage 4 — WEAVE (synthesis)
                                                        └─▶ Scoring + retry (score < 6)
                                                              └─▶ HITL checkpoint (if enabled)
                                                                    └─▶ Workflow Results
                                                                          └─▶ Export: Word / PDF / MD / TXT
```

---

## Core Concepts

**Agents** are specialist AI personas with a name, role, icon, system prompt, model override, per-agent temperature (0.0–2.0), and independent web search behavior. Seven built-in agents ship out of the box. Create unlimited custom agents for any domain.

**Workflows** are ordered agent pipelines with a default prompt template (using `{{placeholders}}`), DAG execution settings, validation, memory toggles, and HITL checkpoints. Selecting a workflow in Compose auto-fills the textarea and shows the live pipeline diagram.

**DAG Execution** runs agents in dependency-staged groups. Search runs first, analysis runs in parallel, synthesis runs last — faster runs and API rate-limit safe.

**Orchestrator** manages the entire pipeline — decomposition, per-agent briefings, quality scoring 1–10, and automatic retries. Advanced Orchestrator mode enables richer briefings and detailed scoring rationale.

**HITL** pauses the pipeline at flagged agents for human review — approve, edit inline, or send feedback for a re-run. Optional audio alert.

**Library** is the RAG document store. Upload files directly or promote items from Captures. Hybrid semantic vector + BM25 search retrieves relevant chunks into agent context.

**Captures** is the inbox for everything sent from the Chrome extension — pages, selections, screenshots, and images. Each item is auto-tagged, vision-analyzed (images), and embedded on arrival.

**Memories** is a persistent key-value store. Agents write `MEMORY[key]: value` during runs. Stored memories inject into agent context on every subsequent run.

**Workflow Results** stores every completed pipeline output. Open any result in a full modal with tabs for Synthesis, Agent Results, Artifacts, and Raw output.

---

## Feature Overview

### Chrome Extension

- **Right-click context menu** on any page: Quick Capture, Open in Compose, Capture Screenshot, Run Workflow (submenu auto-populated from saved workflows)
- **Extension popup**: Send Full Page, Send Selection, Capture Screenshot — with live queue count
- **Image right-click**: Send Image to Nemilia — routes directly to Captures inbox
- **Offline queue** — items captured while Nemilia is closed are saved locally and delivered automatically on next open
- Extension connection status shown in Settings (green connected / grey not detected)

### Captures Inbox

- Live badge counter on the Captures nav item
- Search with live text highlighting across title, summary, tags, and content
- Custom tags — shared global tag pool with Library; filter by tag with auto-hiding pills
- Expand/collapse cards showing type badge, vision/RAG status, tag chips, content preview, and triage row
- Image captures — thumbnail opens combined image + vision analysis viewer
- Multi-select with batch workflow runs
- **Triage actions per item:** → Compose · → Chat · → Workflow · → Library · ↗ Source
- Auto-embed on ingest — text captures auto-chunk and queue for vector embedding on arrival; image captures auto-queue after vision analysis
- Promote to Library carries over computed embeddings — re-embedding skipped

### Chat Mode

- Persistent multi-turn conversations with streaming, auto-titling, and session persistence
- RAG context injection from Library documents
- Memory injection from Memories store
- **Web Search toggle** in the chat context bar — enable live search per message
- Attach captures as context chips directly in Chat
- Provider switch banner — dismissible mid-chat notification when model changes

### Compose & Workflow Mode

- Workflow selector dropdown — selecting auto-fills prompt template and shows inline DAG diagram
- **Compose attachment chips** — attach captures from Captures inbox as inline context cards
- Real-time cost tracking — token count and Est. Cost update live as agents stream
- **Predictive Execution Engine** — pre-run complexity scoring (🟢/🟡/🔴), ambiguity flags, runtime estimate, and HITL suggestions before firing
- Saved prompt chips — click any template to load instantly
- Web Search toggle for direct prompts

### Multi-Agent DAG Orchestration

- 7 built-in specialists: **SCOUT** (research), **LENS** (analysis), **QUILL** (writing), **FORGE** (review), **WEAVE** (synthesis), **NEXUS** (web search), **VISION** (charts & visuals)
- Custom agents: name, role, icon, colour, full system prompt, model override, temperature (0.0–2.0)
- Per-agent web search — any agent can search independently (auto-detect / always / custom query)
- DAG parallel execution — independent agents run simultaneously
- Orchestrator validation: score 1–10, auto-retry below threshold
- Advanced Orchestrator: richer per-agent briefings, detailed rationale, targeted retry prompts
- Auto Workflow — describe a task, the orchestrator picks the right agents and runs automatically

### Human-in-the-Loop (HITL)

- Per-agent and per-workflow HITL checkpoints
- Three review actions: approve, inline edit, or feedback-driven re-run
- Amber pulsing indicator while paused
- Optional audio alert (Settings → Notifications)

### Workflow Builder

- Drag-and-drop agent reordering with live SVG DAG preview
- HITL toggle per agent card
- Prompt template field with `{{placeholder}}` variables
- Per-workflow: validation, DAG mode, memory injection, memory writes, SLM compression

### Library & Document RAG

- Upload PDF, DOCX, TXT, MD, CSV via drag-and-drop or file picker
- **Folder scan** — bulk-import from any local directory (supports `.md .txt .csv .json .html .pdf .js .ts .py .docx`)
- Drop images (PNG, JPG, WEBP, GIF) — vision analysis runs automatically and indexes the result as a searchable RAG document
- 384-dimensional vector embeddings via Transformers.js (`all-MiniLM-L6-v2`)
- Hybrid search: 60% cosine vector similarity + 40% BM25
- 12,000-character context budget per run
- Embeddings persist in IndexedDB — survive page refreshes
- Select Library items for Compose context via the **Library** button in the toolbar
- Obsidian vault support — scans `.md` files, strips `[[wikilinks]]` for cleaner chunks

### Web Search

- 4 providers: Serper (Google), Brave Search, Tavily AI, SearXNG (self-hosted)
- NEXUS runs first in DAG, passes cited results to all downstream agents
- Per-agent web search — any agent can search independently in v2.1
- Inline `[Title](URL)` citations in every output
- Web Search toggle in Chat for individual messages

### Image & Visual Generation

- VISION generates Chart.js charts, SVG diagrams, and HTML infographics — no image API needed
- AI image generation: DALL·E 3, Together AI (FLUX / SD), xAI Aurora, Google Imagen 4, Stability AI SD3, Replicate (FLUX Pro), Fal.ai (FLUX Dev)
- Configure via **Connections → Image Generation**

### Browser-Native AI (WebLLM)

- Run models in-browser across VRAM tiers (0.8 GB to 24 GB)
- WebGPU-accelerated via MLC WebLLM
- HuggingFace model registry browser — load any MLC-compiled model directly
- Models cache locally after first download
- Unload Model button frees GPU VRAM instantly
- **Chrome AI (Gemini Nano)** — zero install, zero API key, on-device chat only. Requires Chrome 127+ with Gemini Nano enabled. Not suitable for workflows.

### Memories

- Persistent key-value store across sessions
- Agents write `MEMORY[key]: value` — all agents can read
- **Memory Writes toggle** — control whether agents write new memories per session
- **Memory Injection toggle** — control whether stored memories inject into context
- Browse, edit, and delete entries in **Data → Memories**

### Workflow Results

- Every completed pipeline output saved automatically
- Open any result in a full overlay modal
- Four tabs: Synthesis (rendered markdown) · Agent Results (with score badges) · Artifacts · Raw
- Export: Word, PDF, Markdown, plain text, Copy
- **⚡ Run as prompt** — send result synthesis to Compose as an attachment for follow-up runs
- Sort by Newest / Oldest / Workflow A–Z

### Workspace & Storage

- File System Access API (Chrome/Edge): sync to a real folder — agents, prompts, workflows saved as plain JSON/Markdown
- IndexedDB fallback (Firefox/Safari) with localStorage as last resort
- Collapsible file browser in sidebar
- Obsidian vault integration — full recursive folder scan with wikilink stripping
- Auto-reconnect on reload via persisted `FileSystemDirectoryHandle`

---

## Tutorials

### Tutorial: Installing the Chrome Extension

1. Download `nemilia-extension.zip` from [GitHub Releases](https://github.com/luislopez1212/Nemilia) and unzip it anywhere
2. Open `chrome://extensions` in Chrome → enable **Developer mode** (top right)
3. Click **Load unpacked** → select the unzipped folder
4. Open **Details** → enable **Allow access to file URLs**
5. Pin the extension from the 🧩 toolbar icon for quick access
6. Open Nemilia — the green **● Extension connected** badge appears in Settings

---

### Tutorial: Capturing with the Extension

**Right-click a page:**
- **Quick Capture** — saves full page text to Captures inbox
- **Open in Compose** — opens Nemilia with the page attached to Compose
- **Capture Screenshot** — takes a screenshot and sends to Captures
- **Run Workflow →** — submenu lists your saved workflows; select one to run it against the page instantly

**Right-click an image:**
- **Send Image to Nemilia** — sends the image directly to Captures inbox for vision analysis

**Extension popup (click toolbar icon):**
- **Send Full Page** — captures full page text
- **Send Selection** — captures highlighted text only
- **Capture Screenshot** — captures the visible tab

**Offline queue:** If Nemilia isn't open, items are saved locally and delivered automatically the next time Nemilia opens. The popup shows a queued item count.

---

### Tutorial: Triaging Captures

1. Go to **Data → Captures** — each item shows type, source, tags, and status badges
2. Click a card to expand — see content preview, vision analysis (images), and triage actions
3. **Triage actions:**
   - **→ Compose** — attaches the item as a context chip in Compose
   - **→ Chat** — opens Chat with the item attached and pre-filled instruction
   - **→ Workflow** — attaches item to Compose and focuses the workflow dropdown
   - **→ Library** — promotes to Library for RAG (carries over embeddings if already processed)
   - **↗ Source** — opens the original URL
4. Use **Search** to find items by title, summary, tags, or content
5. Use **+ Tag** to create and assign tags; filter by tag with the pill row
6. Multi-select items for batch workflow runs

---

### Tutorial: Connecting an AI Provider

Click the gold provider pill in the header → **🚀 Set Up Your AI Provider**.

**Cloud API:** Select a provider → paste your API key → select a model → Save & connect. Keys encrypted AES-256-GCM, never leave your browser except to call the provider.

**Local (Ollama, Jan, LM Studio, Llamafile):** Nemilia auto-detects running local servers. Select the provider → confirm the detected endpoint → select a model → Save.

**WebLLM:** Select Browser AI (WebLLM) → choose a model → Load model. Progress ring shows download. Models cache locally.

**Custom API:** Select Custom API → enter endpoint URL, model ID, optional API key → Save.

Switch providers anytime — keys for all providers are remembered.

---

### Tutorial: Your First Workflow Run

1. Go to **Create → Compose**
2. Select **Research Suite** from the workflow dropdown — the textarea auto-fills with the prompt template and the pipeline diagram appears in the toolbar
3. Edit the prompt to your topic
4. Press `Ctrl+Enter`
5. Watch SCOUT → LENS → QUILL → FORGE → WEAVE execute in parallel DAG stages
6. Live **Est. Cost** and token counter update as agents stream
7. Finished output saved to **Data → Workflow Results** automatically
8. Open the result → export as Word, PDF, or Markdown

---

### Tutorial: Creating Custom Agents

1. **Build → Agents → + New agent**
2. Set: Name, Role, Icon, Colour, System prompt
3. **Model override** — use a different model for this agent than the global provider
4. **Temperature** (0.0–2.0) — lower for review/factual agents, higher for creative/writing agents
5. **Web search** — enable and choose Auto-detect, Always, or set a custom query
6. **⏸ HITL** — check to pause the pipeline at this agent for human review
7. Save → add the agent to any workflow

---

### Tutorial: Building Custom Workflows

1. **Build → Workflows → + New**
2. Name the workflow and write a **Prompt template** using `{{placeholders}}`
3. Add agents from the dropdown. Drag ⠿ handles to reorder. Toggle ⏸ HITL per agent.
4. Configure: validation on/off, DAG mode, memory injection, memory writes, SLM compression
5. Save → appears in the Compose workflow dropdown immediately
6. Selecting it auto-fills the textarea with the template and shows the inline DAG diagram

---

### Tutorial: Human-in-the-Loop Review

Enable HITL on any agent (agent editor → ⏸ HITL) or per workflow (workflow builder → toggle per agent card).

**When the pipeline pauses:**
- ✓ **Approve** — continue as-is
- ✏️ **Edit** — modify the output inline, then continue with your version
- 💬 **Feedback** — type what to fix, re-run that agent, review again

**Audio alert:** Settings → Notifications → enable HITL Sound Alert.

---

### Tutorial: Library & Document RAG

1. **Data → Library** → drag-and-drop files or click Upload (PDF, DOCX, TXT, MD, CSV)
2. For bulk import: click **📂 Import Folder** — scans any directory for all supported types
3. For workspace sync: click **📁 Scan Workspace** — re-scans your connected workspace folder
4. Drop images (PNG, JPG, WEBP, GIF) — vision analysis runs automatically and indexes the result
5. Wait for the **✓ RAG Ready** badge — embeddings complete and persisted
6. In Compose: click **Library** in the toolbar to select documents for the run
7. Relevant chunks (up to 12,000 chars) inject into each agent's context automatically

**Promote from Captures:** Any Capture item with a **→ Library** triage action carries its existing embeddings — no re-processing needed.

---

### Tutorial: Web Search with NEXUS

1. **Tools → Connections → Web Search** → select a provider (Serper recommended) → paste key → Save
2. **Build → Agents** → click **＋ Add NEXUS** (or add NEXUS to any workflow manually)
3. **Build → Workflows** → click **＋ Web Research workflow** to create a pre-configured web research pipeline
4. Run from **Create → Compose** — NEXUS searches live, downstream agents build on cited results

---

### Tutorial: Per-Agent Web Search

Any agent can search the web independently in v2.1 — not just NEXUS.

1. **Build → Agents** → edit any agent → enable **Web search**
2. Choose a mode:
   - **Auto-detect** — searches only when the incoming message signals search intent
   - **Always** — searches on every run
   - **Custom query** — define a fixed query with `{input}` substitution
3. Save → that agent will search independently when it runs

---

### Tutorial: Running Local Models (WebLLM)

1. Click provider pill → **Browser AI (WebLLM)**
2. Choose a model by VRAM tier:
   - ⚠️ Minimum (0.8–2 GB): SmolLM2 1.7B, Llama 3.2 1B
   - ✅ Recommended (4–8 GB): Qwen 2.5 7B ⭐, Llama 3.1 8B
   - 🔥 Enthusiast (12–24 GB): Llama 3.1 70B
3. Or browse the **HuggingFace model registry** directly in the panel
4. Or click **▸ Custom model URL** and paste a HuggingFace repo URL
5. Click **Load model** — progress ring shows download; models cache after first download
6. Click **Unload Model** to free GPU VRAM when switching providers

> **Chrome AI (Gemini Nano):** Select Chrome AI as the provider — no download, no API key, fully on-device. Chat only. Requires Chrome 127+ with the Prompt API flag enabled.

---

### Tutorial: Connecting a Custom API Provider

Any OpenAI-compatible endpoint works — vLLM, LMDeploy, Together AI, Fireworks, LiteLLM, or your own inference server.

1. Provider pill → **Custom API**
2. Enter: Endpoint URL, Model ID, optional API key
3. Set Context window and Max output if known
4. Save — available immediately as a provider option

---

### Tutorial: Memory System

**Writing:** Agents output `MEMORY[key]: value` → stored persistently across sessions.

**Reading:** When Memory Injection is on, all stored memories prepend to each agent's context on every run.

**Toggles (Settings):**
- **Memory Writes** — off to prevent new memories being written during a run
- **Memory Injection** — off for clean-room testing or privacy-sensitive runs

**Managing:** **Data → Memories** → browse, edit, delete any entry.

---

### Tutorial: Prompt Templates

1. **Build → Prompts → + New** → write with `{{placeholders}}` → Save
2. Click any saved prompt chip in Compose to load it instantly
3. Workflow prompt templates auto-fill Compose when that workflow is selected

---

### Tutorial: Workspace & File Management

1. Sidebar → **Open workspace** → select a folder (Chrome/Edge only)
2. Agents, prompts, and workflows sync as plain JSON/Markdown — editable in VS Code, versionable in Git
3. **Library → 📁 Scan Workspace** re-scans for new or changed files
4. **Library → ↻ Sync** updates any modified files
5. Files are never overwritten — Nemilia only writes new content
6. Obsidian vaults supported: `.obsidian`, `.trash`, `.git` folders skipped automatically; `[[wikilinks]]` stripped for cleaner RAG chunks

---

### Tutorial: MCP Tool Execution

1. Start a local MCP server:
```bash
npx -y supergateway --port 8000 --cors --outputTransport streamableHttp --stdio "npx -y @modelcontextprotocol/server-filesystem C:\mcptest"
```
2. **Tools → Connections → MCP Servers → + Add** → URL: `http://localhost:8000/mcp` → Test → Save
3. Create an agent with `TOOLCALL{...}` syntax in its system prompt
4. Add to a workflow → run

| Error | Fix |
|-------|-----|
| `CORS` | Add `--cors` to Supergateway |
| `0 tools` | URL: `/mcp` (streamableHttp) or `/sse` (SSE) |
| `Connection refused` | Confirm port 8000 is running |

---

## Provider Reference

| Provider | Recommended Model | Notes |
|----------|-------------------|-------|
| **Groq** | Llama 3.3 70B | Fastest free tier |
| **OpenRouter** | DeepSeek V3 | 200+ models |
| **Google Gemini** | Gemini 2.5 Flash | 1M context window |
| **Anthropic** | Claude Sonnet 4.6 | Best reasoning |
| **OpenAI** | GPT-4o | Widest tool support |
| **Mistral** | Mistral Large | European data residency |
| **DeepSeek** | DeepSeek V3 | Low cost |
| **Kimi (Moonshot)** | Kimi K2 | Long context |
| **xAI** | Grok 3 | Real-time data |
| **Perplexity** | Sonar Pro | Built-in web search |
| **Ollama** | Any | Local, auto-detected |
| **LM Studio** | qwen3.5 ⭐ | Local, offline vision confirmed |
| **Jan** | Any | Local, cross-platform |
| **Llamafile** | Any | Single-file local model |
| **WebLLM** | Qwen 2.5 7B ⭐ | In-browser, no API key |
| **Custom API** | Any | Any OpenAI-compatible endpoint |
| **Chrome AI** | Gemini Nano | On-device, zero install, chat only |

---

## Architecture

### Single-File Design

The entire application is one `.html` file — HTML, CSS, JavaScript, and embedded assets. No build step, no bundler, no framework.

| Library | Purpose | Loaded When |
|---------|---------|-------------|
| PDF.js (Mozilla) | PDF text extraction | Document upload |
| WebLLM (MLC AI) | Browser-native LLM inference | WebLLM provider selected |
| Transformers.js (Xenova) | Vector embeddings for RAG | Document/capture embedding |
| Chart.js | Chart rendering in VISION | VISION output |

All libraries load on demand. Nothing loads until needed.

### Storage Architecture

```
Three-tier storage (automatic fallback):
  File System API (Chrome/Edge) → IndexedDB → localStorage
```

Capture content and embeddings live in IndexedDB. Workspace data (agents, prompts, workflows, results, memories) syncs to the File System folder when connected.

### Security

- AES-256-GCM key encryption with PBKDF2 200,000 SHA-256 iterations
- Zero telemetry — no analytics, no tracking, no beacons
- CSP `connect-src` locked to an explicit allowlist of known provider endpoints
- **What leaves your browser** (only when you initiate): LLM API calls, search API calls, image API calls, CDN library loads on first use

---

## Browser Compatibility

| Browser | Version | Notes |
|---------|---------|-------|
| Chrome | 121+ | Full support — recommended for File System API and extension |
| Edge | 121+ | Full support including File System API |
| Safari | 17+ | Full support; File System API limited |
| Firefox | 120+ | Full support; no File System API |

---

## Settings Reference

| Setting | Description |
|---------|-------------|
| AI Provider | Global provider and model selection |
| System prompt | Default system prompt for all agents |
| Max output tokens | Upper ceiling for responses |
| Temperature | Global default (0.0–1.0) |
| Max retries | Auto-retry attempts per agent |
| DAG stagger delay | Milliseconds between parallel stage launches |
| Captures preview length | Characters shown in expanded capture card (default 400) |
| HITL Sound Alert | Audio notification when pipeline pauses |
| Advanced: Orchestrator | Planning temp, synthesis temp, validation threshold |
| Reasoning / Think Tags | Show `<think>` blocks as collapsible badge in Chat and Compose |
| Cost Tracking | Show Est. Cost during runs; set cost per 1K tokens |
| Memory Writes | Allow agents to write new memories during runs |
| Memory Injection | Inject stored memories into agent context |
| Browser Extension | Connection status + one-time install instructions |
| Storage | Usage breakdown across File System / IndexedDB / localStorage |
| Browser Compatibility | Runtime compatibility check |
| Hardware | GPU, VRAM, RAM detection for WebLLM model selection |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/⌘ + Enter` | Run compose prompt / Send chat message |
| `Shift + Enter` | New line in compose / chat |
| `Escape` | Close modal |

---

## What's New in v2.1

**Chrome Extension** — right-click any page to capture text, screenshots, or run a workflow directly. Offline queue holds items until Nemilia opens. Image right-click sends directly to Captures.

**Captures Inbox** — dedicated inbox for all extension captures. Auto-tagging, vision analysis on images, BM25 + vector embedding on arrival, and one-click triage to Compose, Chat, Workflow, or Library.

**Vision Pipeline** — images in both Captures and Library are analyzed automatically. Drop a PNG into Library and it becomes a searchable RAG document. Vision status badges track processing state per item.

**Library replaces Documents** — unified RAG store with tags, search, preview modal, and direct promotion from Captures (embeddings carry over, no re-processing).

**Per-agent web search** — any agent can search independently with auto-detect, always-on, or custom query modes. Not just NEXUS.

**Perplexity provider** — four Sonar models with native live web search and inline citations.

**Chrome AI (Gemini Nano)** — fully on-device, zero API key, zero download. Chat only. Requires Chrome 127+ with Prompt API enabled.

**Workflow Results upgraded** — full overlay modal with Synthesis, Agent Results, Artifacts, and Raw tabs. Run as prompt sends output back to Compose.

**Compose attachment chips** — attach captures as inline context cards directly in the compose area.

**Auto-embed on ingest** — text captures embed on arrival; image captures embed after vision analysis. No manual trigger needed.

**Navigation renamed** — Create (Compose, Chat) · Build (Prompts, Agents, Workflows) · Data (Library, Captures, Memories, Workflow Results) · Tools (Connections).

---

## License

Nemilia is released under the **Business Source License 1.1 (BSL 1.1)**.

- ✅ Free for personal, research, and non-commercial use
- ✅ Read, modify, and learn from the source
- ❌ No commercial use, resale, or SaaS deployment without a commercial license
- 🔄 Converts to MIT on 2030-02-27

For commercial licensing: [luis@nemilia.com](mailto:luis@nemilia.com)
