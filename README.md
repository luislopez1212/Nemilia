# Nemilia AI v1.0

**A browser-native AI workspace with multi-agent orchestration, human-in-the-loop review, semantic vector RAG, and visual workflow design — all running in a single HTML file with zero backend.**

*Nemilia (neh-mee-lee-ah) — Nahuatl for "to think, to remember, to imagine"*

---

## What Is This?

Nemilia AI is an entirely client-side AI platform packed into one self-contained HTML file. Open it in any modern browser — no server, no install, no dependencies. It connects to LLM APIs (Groq, OpenRouter, Gemini, OpenAI, Anthropic, Mistral, xAI, DeepSeek) or runs models locally via Ollama, LM Studio, or WebGPU in-browser inference.

The core capability is **multi-agent workflow orchestration**: you define specialist AI agents, wire them into pipelines, and Nemilia runs them in DAG-staged execution with automatic validation, retry loops, and now — **human-in-the-loop checkpoints** where you can review, edit, or redirect any agent's output mid-run.

---

## Quick Start

1. **Open `Nemilia.html`** in Chrome, Edge, or any Chromium browser (Firefox/Safari work too, with minor feature differences).
2. **Click the "🚀 Set Up Your AI Provider" button** in the header. Choose a provider and paste your API key. Groq and OpenRouter offer free tiers.
3. **Go to Compose**, type a prompt, select a workflow, and hit Run. Watch agents execute in real-time with live streaming, validation scores, and search results.

That's it. Everything persists in your browser via IndexedDB (or File System API if you enable it).

---

## Features

### Multi-Agent Orchestration
- **6 built-in agents**: SCOUT (research), LENS (analysis), QUILL (writing), FORGE (QA), WEAVE (synthesis), NEXUS (web search), VISION (charts/images)
- **DAG pipeline execution**: agents run in dependency-ordered stages — NEXUS first (web search), then analysis agents in parallel, then synthesis, then VISION
- **Orchestrator validation**: after each agent completes, an orchestrator LLM scores the output 1–10 and triggers automatic retries if quality is below threshold
- **Custom agents**: create your own specialists with custom system prompts, icons, colours, and optional model overrides

### Human-in-the-Loop (HITL)
- **Per-agent approval checkpoints**: enable HITL on any agent (checkbox in agent editor) to pause the pipeline after that agent completes
- **Three review actions**:
  - ✓ **Approve** — accept the output as-is, pipeline continues
  - ✏️ **Edit** — modify the agent's output directly in an inline editor, then continue
  - 💬 **Send Feedback** — write a note explaining what's wrong; the agent re-runs with your feedback injected, then pauses again for review
- **Per-workflow overrides**: in the workflow builder, toggle ⏸ HITL on/off for each agent independently of its global setting
- **Visual indicators**: amber-pulsing agent cards, dashed HITL nodes in the flow SVG, real-time status in the run log

### Drag-and-Drop Workflow Builder
- **Sortable agent list**: grab the ⠿ handle on any agent in the workflow modal and drag to reorder
- **Inline HITL toggles**: click the ⏸ button on any agent to add/remove a human review checkpoint
- **Live SVG flow preview**: the pipeline diagram updates in real-time as you reorder agents and toggle checkpoints
- **HITL divider lines**: visual "⏸ human review" markers between agents that have HITL enabled

### Semantic Vector RAG
- **Automatic embedding**: when you upload a document, Nemilia chunks it and generates 384-dimensional vector embeddings using `all-MiniLM-L6-v2` via Transformers.js (22MB model, cached after first load)
- **Hybrid search**: queries use a weighted combination of **60% cosine vector similarity + 40% BM25 keyword matching**, delivering both semantic understanding and keyword precision
- **Graceful fallback**: if embeddings aren't available (older docs, or Transformers.js fails to load), the system falls back to pure BM25
- **Manual embed button**: older documents can be embedded on-demand via the "🧠 Embed" button in the Documents panel
- **Progress tracking**: real-time progress bars and status badges during embedding
- **IndexedDB persistence**: embeddings are stored in IndexedDB alongside document content — they survive page refreshes

### Web Search (NEXUS Agent)
- **4 search providers**: Brave Search, Serper (Google), Tavily AI, SearXNG (self-hosted)
- **Automatic integration**: NEXUS runs first in DAG mode, summarises web findings, and passes them to downstream agents
- **Source citations**: NEXUS outputs include `[Title](URL)` inline citations

### Image Generation (VISION Agent)
- **Code-based visuals**: VISION generates Chart.js configs, SVG diagrams, and HTML infographics rendered live in the output panel
- **AI image providers**: optionally connect DALL·E 3, FLUX (via fal.ai or Together AI), Stable Diffusion (via Stability AI), or Recraft V3 for photographic/artistic image generation
- **Auto-prompting**: the orchestrator extracts `IMAGE_PROMPT:` directives from agent outputs and feeds them to image providers

### Document RAG
- **Supported formats**: PDF, DOCX, TXT, MD, CSV
- **Smart chunking**: documents are split into paragraph-level chunks for retrieval
- **Context injection**: only the most relevant chunks (by hybrid vector+BM25 score) are injected into agent prompts — not the full document
- **Multi-document**: upload multiple documents; select which are active per conversation
- **Budget management**: 12,000 character budget across all active documents, distributed proportionally

### Browser-Native AI (WebGPU)
- **Local inference**: run Llama, Gemma, Phi, Qwen, and other models directly in your browser via WebGPU — no API key needed
- **Powered by WebLLM**: uses MLC's WebLLM library for GPU-accelerated in-browser inference
- **Model selector**: choose from quantised models (1B–8B parameters) optimised for browser performance
- **Progress tracking**: real-time download and loading progress during model initialization

### Persistent Memory
- **Cross-session memory**: agents can write `MEMORY[key]: value` in their outputs; these persist across runs
- **Memory injection**: all stored memories are automatically included in agent context
- **Manual management**: view, edit, and delete memory entries in the Memory panel

### Additional Features
- **Prompt templates**: save reusable prompt templates with `{{variable}}` placeholders
- **PDF export**: generate downloadable PDF reports from workflow outputs
- **Markdown rendering**: full markdown support in output display (headers, code blocks, tables, lists)
- **Run statistics**: real-time token count, cost estimate, elapsed time, and per-agent scores
- **Dark theme**: navy/gold colour scheme designed for extended use
- **Encrypted key storage**: API keys encrypted with AES-256-GCM using 200k-iteration PBKDF2

---

## Architecture

### Single-File Design
Everything — HTML, CSS, JavaScript, embedded assets — lives in one `.html` file. There is no build step, no bundler, no framework. External libraries are loaded from CDNs at runtime:
- **PDF.js** (Mozilla) — PDF text extraction
- **WebLLM** (MLC AI) — browser-native LLM inference
- **Transformers.js** (Xenova) — embedding model for vector RAG
- **Chart.js** — chart rendering in VISION outputs

### Data Storage
Three storage tiers with automatic fallback:
1. **File System Access API** (Chrome/Edge) — workspace directory on disk
2. **IndexedDB** — large data (documents, embeddings, content)
3. **localStorage** — settings, agent configs, workspace metadata

### Security Model
- API keys encrypted at rest with AES-256-GCM
- Key derivation via PBKDF2 with 200k iterations
- Keys never leave the browser except to the provider's API endpoint
- Hardened XSS prevention via `esc()` sanitisation on all user-facing content
- Content Security Policy meta tag
- Colour value sanitisation to prevent injection via style attributes

---

## Provider Setup

| Provider | Free Tier | Recommended Model | Setup Link |
|----------|-----------|-------------------|------------|
| **Groq** | Yes (generous) | Llama 3.3 70B | [console.groq.com](https://console.groq.com) |
| **OpenRouter** | Yes (limited) | DeepSeek V3 | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **Google Gemini** | Yes | Gemini 2.5 Flash | [aistudio.google.com](https://aistudio.google.com/apikey) |
| **Anthropic** | No | Claude Sonnet 4 | [console.anthropic.com](https://console.anthropic.com) |
| **OpenAI** | No | GPT-4.1 | [platform.openai.com](https://platform.openai.com) |
| **Mistral** | No | Mistral Large | [console.mistral.ai](https://console.mistral.ai) |
| **xAI** | No | Grok 3 | [console.x.ai](https://console.x.ai) |
| **DeepSeek** | Yes | DeepSeek V3 | [platform.deepseek.com](https://platform.deepseek.com) |
| **Ollama** | Local | Any | [ollama.com](https://ollama.com) |
| **WebGPU** | Local | Llama 3.2 3B | Built-in (Chrome 121+) |

---

## Workflow Execution Flow

```
User Prompt
    │
    ▼
┌─────────────┐
│ ORCHESTRATOR │ ← Decomposes prompt into agent subtasks
└──────┬──────┘
       │
       ▼
┌──────────────┐
│   NEXUS      │ ← Web search (if included)
│  🌐 Stage 1  │
└──────┬───────┘
       │ ⏸ HITL checkpoint (if enabled)
       ▼
┌──────────────────────────────┐
│  SCOUT  │  LENS  │  QUILL   │ ← Analysis agents (parallel)
│       🔍 Stage 2 📊         │
└──────────┬───────────────────┘
           │ ⏸ HITL checkpoint (if enabled)
           ▼
┌──────────────┐
│    WEAVE     │ ← Synthesis
│  ⚡ Stage 3   │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   VISION     │ ← Charts, diagrams, images
│  🎨 Stage 4  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ ORCHESTRATOR │ ← Synthesises final report
└──────┬───────┘
       │
       ▼
   Final Output
   (Markdown + Charts + Images + PDF)
```

Each agent's output is validated by the orchestrator (score 1–10). Scores below 6 trigger automatic retries (up to 2). HITL checkpoints pause execution and present the output for human review.

---

## HITL Workflow Example

1. Create a workflow with SCOUT → LENS → WEAVE
2. Enable HITL on LENS (the analysis agent)
3. Run the workflow with a research prompt
4. SCOUT completes automatically (research phase)
5. LENS completes — **pipeline pauses** with amber-pulsing review panel
6. You review LENS's analysis. Options:
   - **Approve**: analysis looks good → pipeline continues to WEAVE
   - **Edit**: fix a factual error in the textarea → pipeline continues with your corrected version
   - **Feedback**: type "Focus more on competitive dynamics, less on market size" → LENS re-runs with your feedback, pauses again for review
7. WEAVE synthesises the final report using the reviewed analysis

---

## File Structure

```
Nemilia.html          # The entire application (single file)
README.md               # This file
```

When using File System API, Nemilia creates a workspace directory:
```
workspace/
├── agents/             # Agent configs as JSON
├── prompts/            # Prompt templates as Markdown
├── workflows/          # Workflow configs as JSON
├── docs/               # Uploaded document content
├── outputs/            # Generated reports
├── images/             # AI-generated images
├── files/              # Workspace files
└── README.md           # Auto-generated workspace readme
```

---

## Browser Compatibility

| Feature | Chrome 121+ | Edge 121+ | Firefox | Safari |
|---------|-------------|-----------|---------|--------|
| Core functionality | ✅ | ✅ | ✅ | ✅ |
| File System API | ✅ | ✅ | ❌ (IndexedDB) | ❌ (IndexedDB) |
| WebGPU (local LLM) | ✅ | ✅ | ⚠️ (limited) | ❌ |
| Vector RAG (Transformers.js) | ✅ | ✅ | ✅ | ✅ |
| PDF parsing | ✅ | ✅ | ✅ | ✅ |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/⌘ + Enter` | Run prompt / Send message |
| `Ctrl/⌘ + K` | Focus compose input |

---

## Privacy & Security

- **Zero telemetry**: no analytics, no tracking, no data collection
- **Client-side only**: all processing happens in your browser
- **Encrypted keys**: API keys stored with AES-256-GCM encryption
- **No server**: the HTML file can run from `file://` protocol (though CDN libraries need internet)
- **Your data stays yours**: documents, memory, and outputs never leave your browser except when sent to the LLM provider you choose

---

## Changelog

### v1.0 (Current — Initial Release)
- **Human-in-the-Loop (HITL)**: per-agent approval checkpoints with approve/edit/feedback actions
- **Drag-and-Drop Workflow Builder**: sortable agent list with live SVG flow preview
- **Semantic Vector RAG**: hybrid vector (Transformers.js) + BM25 search with automatic document embedding
- **Browser-native AI**: WebGPU/WebLLM local inference
- **5 image providers**: DALL·E, FLUX, Stable Diffusion, Recraft
- **DAG pipeline execution**: orchestrator validation with auto-retry
- **Document RAG**: PDF, DOCX, TXT, MD, CSV support with smart chunking
- **Persistent memory system**: cross-session agent memory
- **4 search providers**: Brave, Serper, Tavily, SearXNG
- **12 LLM providers**: Groq, OpenRouter, Gemini, OpenAI, Anthropic, Mistral, xAI, DeepSeek, Ollama, LM Studio, Jan, Llamafile
- **Navy/gold visual design**
- **AES-256-GCM encrypted key storage**

---

## License

MIT — free to use, modify, and distribute.

---

*Built with care. No frameworks were harmed in the making of this application.*
