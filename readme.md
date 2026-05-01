<div align="center">
  <img src="full_logo.png" alt="Nemilia AI Workspace" width="340" />

  <h1>Nemilia — AI OS for the Browser · v2.2</h1>

  <p><strong>One file. Any model. No server.</strong></p>

  <p>
    Multi-profile encrypted workspace &nbsp;·&nbsp; Multi-agent orchestration &nbsp;·&nbsp; Skills system &nbsp;·&nbsp; Autonomous MCP tasks<br/>
    Chrome extension capture &nbsp;·&nbsp; Document RAG &nbsp;·&nbsp; Live web research &nbsp;·&nbsp; Offline local models &nbsp;·&nbsp; Zero backend &nbsp;·&nbsp; 100% client-side
  </p>

  <p>
    <a href="https://nemilia.com">nemilia.com</a> &nbsp;·&nbsp;
    <a href="mailto:luis@nemilia.com">luis@nemilia.com</a>
  </p>

  <img src="https://img.shields.io/badge/version-2.2-gold" alt="version" />
  <img src="https://img.shields.io/badge/license-BSL_1.1-orange" alt="license" />
  <img src="https://img.shields.io/badge/backend-none-brightgreen" alt="no backend" />
  <img src="https://img.shields.io/badge/install-open%20HTML%20file-brightgreen" alt="install" />

</div>

---

Nemilia turns any browser into a complete AI production environment. Capture content from the web with the Chrome extension, route it through multi-agent workflows, search your document library, run autonomous MCP-powered tasks, and deliver finished results — all inside a single self-contained HTML file with no server, no install, and no data leaving your machine.

v2.2 adds encrypted multi-profile accounts, a dashboard, a full skills system, AI-assisted creation for every asset type, a curated MCP catalog, a built-in tool tester, autonomous Tasks, and extensive mobile improvements.

*Nemilia (neh-mee-lee-ah) — Nahuatl for "to think, to remember, to imagine"*

---

## Table of Contents

- [What Is Nemilia?](#what-is-nemilia)
- [Quick Start](#quick-start)
- [The v2.2 Pipeline](#the-v22-pipeline)
- [Navigation](#navigation)
- [Feature Overview](#feature-overview)
  - [Profiles and Encrypted Workspace](#profiles-and-encrypted-workspace)
  - [Dashboard](#dashboard)
  - [Compose](#compose)
  - [Chat](#chat)
  - [Agents](#agents)
  - [Prompts](#prompts)
  - [Skills](#skills)
  - [Tasks](#tasks)
  - [Workflows](#workflows)
  - [Captures](#captures)
  - [Library and Document RAG](#library-and-document-rag)
  - [Memories](#memories)
  - [Workflow Results](#workflow-results)
  - [Connections](#connections)
  - [AI Generators](#ai-generators)
- [AI Provider Modes](#ai-provider-modes)
  - [Provider API](#provider-api)
  - [Local Server](#local-server)
  - [In-Browser](#in-browser)
- [Tutorials](#tutorials)
  - [Creating Your First Profile](#tutorial-creating-your-first-profile)
  - [Navigating the Dashboard](#tutorial-navigating-the-dashboard)
  - [Connecting an AI Provider](#tutorial-connecting-an-ai-provider)
  - [Your First Workflow Run in Compose](#tutorial-your-first-workflow-run-in-compose)
  - [Using Chat](#tutorial-using-chat)
  - [Popping Out Chat](#tutorial-popping-out-chat)
  - [Creating Custom Agents](#tutorial-creating-custom-agents)
  - [Using and Creating Skills](#tutorial-using-and-creating-skills)
  - [Running a Task with MCP Tools](#tutorial-running-a-task-with-mcp-tools)
  - [Building Custom Workflows](#tutorial-building-custom-workflows)
  - [Human-in-the-Loop Review](#tutorial-human-in-the-loop-review)
  - [Installing the Chrome Extension](#tutorial-installing-the-chrome-extension)
  - [Capturing with the Extension](#tutorial-capturing-with-the-extension)
  - [Triaging Captures](#tutorial-triaging-captures)
  - [Library and Document RAG](#tutorial-library-and-document-rag)
  - [Web Search with NEXUS](#tutorial-web-search-with-nexus)
  - [Image Generation and Custom Endpoint](#tutorial-image-generation-and-custom-endpoint)
  - [MCP — Catalog, Custom Servers, Tool Tester, and Templates](#tutorial-mcp)
  - [Memory System](#tutorial-memory-system)
  - [AI Generators](#tutorial-ai-generators)
  - [Running Local Models](#tutorial-running-local-models)
  - [Running In-Browser Models](#tutorial-running-in-browser-models)
  - [Connecting a Custom API Provider](#tutorial-connecting-a-custom-api-provider)
  - [Workspace and File Management](#tutorial-workspace-and-file-management)
- [Provider Reference](#provider-reference)
- [Architecture](#architecture)
- [Security and Privacy](#security-and-privacy)
- [Browser Compatibility](#browser-compatibility)
- [Settings Reference](#settings-reference)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [What's New in v2.2](#whats-new-in-v22)
- [License](#license)

---

## What Is Nemilia?

Nemilia is an entirely client-side AI platform in a single self-contained HTML file. No server, no installer, no account required, no database. Open one file in a browser and get a full multi-agent AI workspace.

Every piece of data — agents, prompts, workflows, skills, tasks, memories, documents, chat history, API keys — lives in your browser's storage or in a local folder you choose, encrypted per profile. Nothing is sent anywhere except the API calls you explicitly initiate.

---

## Quick Start

1. **Download** `Nemilia-v2.2.html` from [GitHub](https://github.com/luislopez1212/Nemilia)
2. **Open** it in Chrome 121+ or Edge 121+
3. **Create a profile** — enter a name and password; your workspace is encrypted at rest with AES-256-GCM
4. **Connect a provider** — click the provider pill in the header, select a provider, paste your API key, and save
5. **Run** — go to Compose, pick a workflow or write a prompt, and click **Run**

No config files, no environment variables, no package installs. The setup wizard appears once; every subsequent open goes straight to your workspace.

**Important (Chrome Extension):** If you use the Chrome extension with Nemilia opened as a local file, you **must** enable **"Allow access to file URLs"** in the extension's details (chrome://extensions) after installation.

**Optional:** Install the Chrome extension for web capture — see the [tutorial below](#tutorial-installing-the-chrome-extension).

---

## The v2.2 Pipeline

```
Web page / file / image
        |
        v
  Chrome Extension — right-click capture or popup
        |
        v
  Captures Inbox
  vision analysis · auto-tagging · BM25 + vector embedding
        |
        v
  Triage: Compose / Chat / Workflow / Library
        |
        v
  Multi-Agent DAG Pipeline
  Orchestrator → per-agent briefings
        |
   +----|------+
   v           v
 Stage 1    Stage 2  (parallel stages)
 NEXUS     SCOUT · LENS · QUILL
   |           |
   +----|------+
        v
     Stage 3 — FORGE (review)
        v
     Stage 4 — WEAVE (synthesis)
        v
  Score + retry (below threshold)
        v
  HITL checkpoint (if enabled)
        v
  Workflow Results
  export: Word / PDF / MD / TXT / HTML
```

Tasks run a separate path: a single LLM agent calls MCP tools autonomously in a loop until the goal is complete, without going through the workflow DAG.

---

## Navigation

The sidebar is organized into four groups matching the logical flow of using the app:

**Home** — Dashboard

**Create** — Compose, Chat

**Build** — Agents, Prompts, Skills, Tasks, Workflows

**Data** — Captures, Library, Memories, Workflow Results

**Tools** — Connections

The profile row at the bottom of the sidebar shows your avatar initial, display name, and a logout/switch action.

---

## Feature Overview

### Profiles and Encrypted Workspace

v2.2 introduces a full multi-profile system. On first launch you create a profile with a name and password. The workspace is serialized, encrypted under your password key, and stored in the browser. No data is accessible without the password. A one-time recovery code is generated at creation and shown once — save it.

Each profile is fully isolated: separate agents, prompts, workflows, skills, tasks, memories, API keys, MCP servers, and preferences. The active profile is tracked in `sessionStorage`; switching profiles or logging out zeroes all in-memory workspace data before the login overlay appears, preventing cross-profile data leakage. Each profile also has its own theme preference.

---

### Dashboard

The Dashboard is the default post-login landing screen (configurable in Settings). It shows:

- **Profile card** — your display name, active provider name, and active model
- **Stats grid** — live counts for Chats, Results, Captured, Memory, Library, Agents, Tasks, and MCP servers; each tile is a navigation shortcut
- **Quick-action tiles** — one-click navigation to Chat, Compose, Tasks, Library, Connections, and Results
- **Recent Chats** — last four conversations, sorted by recency, with direct links
- **Recent Workflow Results** — last four results with direct links

The provider pill on the dashboard stays in sync with the global provider state without requiring a page reload.

---

### Compose

Compose is the primary production surface. It combines a prompt input, workflow selection, context controls, and a live multi-agent execution view.

**Input and controls:**
- Workflow selector dropdown — pick any saved workflow or run a direct prompt with no workflow
- Prompt input — plain text; `{{variable}}` placeholders in a selected workflow prompt open a fill-in dialog before run
- Skills chip — opens the skill selector; badge shows how many are active
- Memory chip — shows current memory injection state; click to toggle
- Attachment button — attach existing documents from the Library or Captures to the run
- 📎 Paperclip button — upload new files directly from compose; files are added to the Library and attached as context in one step
- Drag-and-drop zone — drop files anywhere on the compose surface for the same one-step ingest-and-attach flow; paste from clipboard (Ctrl+V / Cmd+V) also supported
- Search pill — shows web search status; click to toggle for this run
- MCP pill — shows MCP connection status

**Run output:**
- Real-time agent cards showing name, role, status (queued, running, done), streaming text, thinking badge for reasoning models, validation score (1–10), and estimated token and cost usage
- Full-page toggle to maximize the output panel
- Synthesis displayed below all agent cards when the run completes
- Export buttons: Word, PDF, Markdown, plain text, HTML
- Save result button — saves to Workflow Results

**Keyboard shortcut:** `Escape` to cancel.

---

### Chat

Chat is a persistent multi-turn conversational interface. All conversations are saved per profile and sorted by recency.

**Layout:**
- Left panel: chat list, + New chat button, Pop out button, Clear chats button
- Main area: message thread, streaming assistant responses, context bar at the top of the input area

**Context bar chips** — each chip is independently toggleable per session:
- **Library** — opens a document picker modal; selected documents are injected as RAG context into every message
- **Captures chips** — captures triaged to chat appear as removable chips; their text content is injected as context
- **Memory ON/OFF** — toggles memory injection for this session
- **Web Search ON/OFF** — toggles live web search before each message (requires a configured search provider)
- **MCP Tools** — toggles MCP tool calling in chat; when enabled, the chip shows the connected server names; the LLM can call tools using the same `TOOL_CALL` format as workflow agents
- **Skills chips** — enabled chat-scoped skills appear as individual toggleable chips

**Attaching files to Chat:** drag files onto the chat area, paste them into the input (Ctrl+V / Cmd+V), or click the 📎 paperclip button left of the textarea. Dropped/pasted/picked files are added to the Library (full ingest: parse → chunk → embed → IDB) and auto-attached as context for this chat. A blurred drop overlay with a bob-animated glyph appears on drag-enter and flashes green on success.

**During a message:** a stop button replaces the send button while streaming. The model's response streams directly into the chat thread with a live status badge — **Working… → Generating… → Responded in Ns** — that ticks elapsed time every second. Reasoning model output (`<think>` blocks) renders as a collapsible "Thinking… → Thought for Ns" badge. Provider switches mid-conversation are handled gracefully with a silent bridging note injected into the context so the new model understands the prior history.

**Chrome AI:** Per-chat sessions are created and reused for Gemini Nano, giving it true multi-turn context within a conversation.

---

### Chat — Pop Out

The **Pop out** button opens chat in a dedicated browser window (`?chat=1`). The popout hides the sidebar, header, and chat list panel, giving a clean full-height chat interface.

The popout has its own mini control bar at the top with:
- Nemilia wordmark
- Provider button — opens the provider modal to switch model
- Memory pill — shows Memory ON/OFF state; click to toggle
- Copy button — copies selected text to clipboard
- Save to Library button — saves all assistant messages from the current conversation as a Library document
- + New button — starts a new conversation
- Clear button — clears all chat history

The popout shares the same workspace state as the main window. Both windows stay in sync.

---

### Agents

Agents are specialist AI personas with a name, role, icon, system prompt, model override, per-agent temperature (0.0–2.0), and independent capability flags. They are the building blocks of every workflow.

**Built-in agents:** SCOUT (research), LENS (analysis), QUILL (writing), FORGE (review), WEAVE (synthesis), NEXUS (web search), VISION (chart and diagram generation), TOOLS (MCP tool execution).

**Per-agent capabilities:** web search toggle, vision toggle, MCP tools toggle, memory injection toggle, HITL flag.

**Model override:** each agent can use a different model than the global provider, enabling mixed-model pipelines within a single workflow run.

---

### Prompts

Prompts are saved, reusable prompt templates with an optional `{{variable}}` placeholder system. Select a prompt in Compose — if it contains variables, a fill-in dialog opens before the prompt is inserted. Tags and descriptions help organize large prompt libraries.

---

### Skills

Skills are reusable instruction sets injected into agent context at run time. They change how the AI responds — tone, format, analytical stance — without modifying the agent or workflow definition.

Ten skills ship pre-loaded, all disabled by default:

| Skill | Scope | Purpose |
|-------|-------|---------|
| Be Concise | All | Removes preamble and filler; forces direct answers |
| Formal Tone | All | Removes contractions; enforces professional register |
| Cite Sources | All | Requires inline citations or explicit uncertainty flags on every factual claim |
| Rich Markdown | All | Enforces headers, tables, bullet lists, and code blocks |
| Step-by-Step | All | Numbered steps with action verb, instruction, and expected outcome |
| Code Expert | All | Complete code first, never truncated; comments every non-obvious line |
| Devil's Advocate | Compose | Challenges every claim with a counter-argument |
| Research Mode | Chat | Maps established vs. debated claims; flags knowledge gaps |
| Executive Summary | Compose | Leads every response with a 3-sentence summary before detail |
| Structured Output | All | Provides a JSON or YAML block alongside prose for any data or comparison |

Skills appear as chips in the Compose bar and as individual toggleable chips in the Chat context bar. Create skills manually or generate them with AI.

---

### Tasks

Tasks are autonomous, goal-driven operations that use connected MCP tools to complete a stated objective. Unlike workflows, a task does not route through multiple agents — a single LLM agent calls tools in a loop, decides what to call next based on results, and stops when the goal is done.

**Each task has:**
- A **name** and a **goal** — a plain-text description of what to accomplish
- A **Run** button — executes immediately against your connected MCP servers
- A **live execution log** — streams each tool call and result in real time inside a collapsible log panel below the task card
- A **pulse-border animation** on the task card while running; the Tasks nav item shows an "Executing" badge
- A **run history** — all previous runs stored with timestamp, status, and full output; expandable per task
- A **Run in Workflow** option — attach the task result to a workflow for further processing
- **Save to Library** — saves the task result as a Library document
- **Make Agent from Task** — creates a reusable TOOLS agent pre-configured with the task goal as its system prompt
- **AI Suggest** — an AI button that refines your goal text and adds relevant tool names from your connected servers
- **AI Generate** — describe the goal in plain language; AI writes a complete task configured for your connected tools

Tasks require at least one connected MCP server and a configured AI provider. The task agent uses the same `TOOL_CALL` format as workflow agents and has access to the full connected tool set.

---

### Workflows

Workflows are directed acyclic graphs (DAGs) of agents that execute in parallel stages. An Orchestrator plans the run, launches stages, validates each agent output (1–10 score), retries below the threshold, and synthesizes a final result.

Workflow behavior is configurable: validation on or off, memory injection, stagger delay between parallel launches, and per-agent HITL flags. The Workflow Builder provides a visual drag-and-drop editor for creating and editing DAGs.

Three default workflows ship: Research Suite, Web Research Suite, and MCP Research + Synthesis.

---

### Captures

All content captured via the Chrome extension lands in Captures. Each capture is auto-tagged, BM25-indexed, and vector-embedded on arrival. Images receive automatic vision analysis if a vision-capable model is active. Each capture card shows the title, source URL, type badge (text, screenshot, image), and processing status badges (BM25, Vector, Vision, RAG Ready).

**Triage actions per capture:** send to Compose input, send to Chat, send to a specific workflow, add to Library. Bulk selection supports multi-capture triage. A search bar filters the inbox.

---

### Library and Document RAG

Upload documents (PDF, DOCX, TXT, Markdown, CSV), code files (JS, TS, Python, Go, Rust, Java, C/C++, Ruby, PHP, HTML, CSS, JSON, YAML, XML, SQL, Shell, TOML, R), and images (PNG, JPG, WEBP, GIF) to the Library. Three ingest entry points share the same pipeline: the Library drop zone, drag-drop / paste / paperclip inside Chat or Compose (also attaches to the current session), and the Chrome extension. Documents are chunked, BM25-indexed, and vector-embedded. The RAG TopK setting (default: 10) controls how many chunks are retrieved per query. Relevant chunks inject into agent context automatically for any workflow or chat session with Library access enabled.

Library images receive vision analysis. A search bar runs a live hybrid BM25 + vector search across all active documents. Toggle individual documents active or inactive to control which are available to agents.

---

### Memories

Agents write key-value facts during runs using `MEMORY[key]: value` syntax anywhere in their output. Memories persist per profile and are available to future runs.

Memory writes and injection are independently toggleable in Settings — both default to off. The Pick Memories button lets you select exactly which entries get injected rather than injecting all. A memory chip in the Compose bar reflects the current injection state and can be toggled directly from Compose.

---

### Workflow Results

Every completed workflow run saves a full result: title, timestamp, all agent outputs, validation scores, and synthesis. Results are searchable and sortable. The Result Viewer has four tabs: Synthesis, Agent Results, Artifacts, and Raw. Any result can be sent back to Compose as a new prompt with one click.

Export formats: PDF, DOCX (Word), Markdown, plain text, HTML.

---

### Connections

Connections manages three categories of external integrations:

**MCP Servers** — connect any Model Context Protocol server. A curated catalog provides one-click connection for popular integrations (GitHub, Zapier, Exa, and others) with pre-filled URLs and per-service auth guidance. Add custom servers manually; transport type (streamable HTTP, SSE, HTTP) is auto-detected on connection. Auth tokens are stored in IndexedDB only — never in `localStorage`. A built-in Tool Tester lets you pick a server and tool, edit JSON arguments pre-populated from the tool's input schema, run the tool, and inspect the output. Server templates save name and URL (never token) as chips for quick reconnection.

**Web Search** — connect Serper, Brave, Tavily, or a self-hosted SearXNG instance. The search provider is used by NEXUS-enabled agents in workflows and by the web search toggle in Chat.

**Image Generation** — connect DALL-E 3, Stable Diffusion, Flux, or any OpenAI-compatible image endpoint as a custom provider. Image keys are stored separately from text provider keys with automatic fallback. The VISION agent generates charts, SVG diagrams, and HTML infographics using the text LLM — no image API key required for those.

---

### AI Generators

v2.2 adds AI-assisted creation for every asset type. Each generator takes a plain-language description and produces a complete, ready-to-use object:

- **Generate Agent** — describe the specialist; AI writes the name, role, and full system prompt
- **Generate Prompt** — describe the need; AI writes a reusable template with `{{variable}}` placeholders
- **Generate Workflow** — describe the goal; AI builds a multi-step DAG using your existing agents
- **Generate Task** — describe the goal; AI writes the task name and goal referencing your connected tool names
- **Generate Skill** — describe the behavior; AI writes the name, description, and instruction prompt; opens the skill editor pre-filled

All five generators use your configured AI provider.

---

## AI Provider Modes

### Provider API

Remote endpoints; API key required.

| Provider | Key source |
|----------|-----------|
| Groq | console.groq.com |
| OpenAI | platform.openai.com |
| Anthropic | console.anthropic.com |
| Google Gemini | aistudio.google.com |
| OpenRouter | openrouter.ai/keys |
| Mistral | console.mistral.ai |
| DeepSeek | platform.deepseek.com |
| xAI Grok | console.x.ai |
| Kimi (Moonshot) | platform.moonshot.cn |
| Fireworks AI | fireworks.ai/api-keys |
| Perplexity | perplexity.ai/settings/api |
| Custom API | Any OpenAI-compatible endpoint |

### Local Server

A separate application runs on your machine serving an OpenAI-compatible API on `localhost`. Nemilia connects over HTTP — no API key required. The model runs inside the local app; Nemilia auto-detects whichever is running.

| App | Default port | Auto-detect endpoint |
|-----|-------------|----------------------|
| Ollama | 11434 | `http://localhost:11434/v1/models` |
| LM Studio | 1234 | `http://localhost:1234/v1/models` |
| Jan | 1337 | `http://localhost:1337/v1/models` |
| Llamafile | 8080 | `http://localhost:8080/v1/models` |

All four pass `max_tokens: -1` to Nemilia, which tells the app to let the local server generate to end-of-sequence without a token cap.

### In-Browser

No separate app, no local server, no API key. Inference runs inside the browser tab.

**WebLLM (Browser / WebGPU)** — MLC-compiled models run in the browser GPU via WebGPU. Select a model, click Load, and it downloads once and caches in the browser. Requires Chrome 121+ or Edge 121+ with hardware acceleration enabled.

| Model | VRAM | Notes |
|-------|------|-------|
| SmolLM2 1.7B | 1.2 GB | Compact, fast |
| Llama 3.2 1B | 0.8 GB | Fastest, minimal tasks |
| Llama 3.2 3B | 2.5 GB | Simple workflows |
| Gemma 2 2B | 1.4 GB | Google compact |
| Phi 3.5 Mini | 3.7 GB | Strong instruction following |
| Qwen 2.5 3B | 1.9 GB | Multilingual, fast |
| Qwen 2.5 7B | 5.1 GB | Recommended — best quality/size ratio |
| Llama 3.1 8B | 5.0 GB | Strong general purpose |
| Mistral 7B | 4.1 GB | Strong reasoning |
| DeepSeek R1 7B | 5.1 GB | Best in-browser reasoning |
| Gemma 2 9B | 6.4 GB | High quality, needs 8 GB GPU |
| Llama 3.1 70B | 24 GB | Enthusiast only, 24 GB+ GPU |

Switching away from WebLLM unloads the engine automatically to free GPU memory.

**Chrome AI (Gemini Nano)** — uses Chrome's native `LanguageModel` API. Gemini Nano is already installed on the device inside Chrome; no download needed. Enable at `chrome://flags/#prompt-api-for-gemini-nano`. Requires Chrome 127+ desktop. Suitable for on-device chat; does not support the full workflow pipeline. Per-chat sessions are created and reused for true multi-turn context.

---

## Tutorials

---

### Tutorial: Creating Your First Profile

On first launch Nemilia shows the profile creation screen.

1. Enter your name — this is your display name in the sidebar and dashboard
2. Choose a password (minimum 6 characters) and confirm it
3. Click **Create Account & Continue**
4. A one-time **recovery code** is shown — copy it and store it somewhere safe. It is shown once only. It restores a baseline snapshot if you ever forget your password
5. You are now logged in with an encrypted workspace

**To add a second profile:** click the profile row at the bottom of the sidebar → in the login overlay click **+ New profile** → follow the same creation flow. Each profile is fully isolated.

**To switch profiles:** click the sidebar profile row — you are logged out immediately, all in-memory data is cleared, the profile selector appears — click the target profile and enter its password.

**To recover a forgotten password:** on the login screen click **Forgot password?** → **Use recovery code** → enter the code. This restores the baseline snapshot from the time the profile was created. Work saved after that point requires the original password.

---

### Tutorial: Navigating the Dashboard

After login the Dashboard opens by default. The profile card at the top shows your name, the active provider, and active model. The stats grid shows live counts for each section — click any tile to navigate there. Quick-action tiles give one-click access to every major section. Recent Chats and Recent Workflow Results show the last few items with direct links.

To disable the dashboard as the default landing screen: **Settings → Show Dashboard after login → OFF**. Compose becomes the landing screen.

---

### Tutorial: Connecting an AI Provider

1. Click the **provider pill** in the header bar (shows current provider or "Set Up Provider")
2. In the provider modal, select a tier tab: All, Local, etc.
3. Click a provider card — the model grid updates on the right
4. Select a model
5. Paste your API key in the key field and click **Save key**
6. Click **Save provider**

The provider pill turns active and shows the provider and model name.

**To refresh the model list:** click **Refresh Models** inside the modal. Newly discovered models not in the built-in list appear with a star badge.

---

### Tutorial: Your First Workflow Run in Compose

1. Open **Compose** from the sidebar
2. Click the workflow selector and pick a workflow — **Research Suite** is a good starting point
3. Type your topic in the prompt input
4. Optionally toggle skills or attach a document using the chips in the input bar
5. Press **Run**
6. Agent progress cards appear in real time, each showing status, streaming output, validation score, and token usage
7. When all stages complete the synthesis appears below the agent cards
8. Use the export buttons (Word, PDF, MD, TXT) or click **Save result** to store it

---

### Tutorial: Using Chat

1. Open **Chat** from the sidebar
2. Click **+ New chat** to start a conversation
3. Type a message and press `Enter` or the send button

**Adding context to a conversation:**
- Click the **Library** button in the context bar above the input to pick documents — selected documents inject RAG chunks into every message
- Captures triaged to chat appear as chips in the context bar; click the X on any chip to remove it
- Click the **Memory** chip to toggle memory injection on or off for this session
- Click the **Web Search** chip to toggle live web search before each message
- Click the **MCP Tools** chip to toggle tool calling — when enabled the LLM can call your connected MCP servers using `TOOL_CALL` blocks; results are returned inline
- Click individual **Skill chips** to toggle behavior modifiers on or off

While the model is responding a stop button appears — click it to cancel the stream at any point. Reasoning model thinking is shown as a collapsible badge above the answer.

**Managing conversations:** the chat list on the left is sorted newest first. Click any conversation to load it. Click the X on a chat item to delete it. Click **Clear chats** to delete all conversations (with confirmation).

---

### Tutorial: Popping Out Chat

Click the **Pop out** button next to **+ New chat** in the chat sidebar header. A new browser window opens showing only the chat interface — no sidebar, no navigation header, no chat list.

The popout mini bar at the top contains:
- **Provider button** — click to open the provider modal and switch model
- **Memory pill** — shows current injection state; click to toggle
- **Copy** — copies selected text from the chat to clipboard
- **Save to Library** — saves all assistant messages in the current conversation as a new Library document
- **+ New** — starts a new conversation
- **Clear** — clears all chat history (with confirmation)

The popout is useful as a persistent side window while working in the main Nemilia window or in other applications.

---

### Tutorial: Creating Custom Agents

1. Go to **Build → Agents → New agent**
2. Enter a name (displayed in workflow cards, e.g. ANALYST), a role, and a system prompt — this is the full instruction the model receives as its system message
3. Set an optional model override to use a different model than the global provider for this agent
4. Set temperature: lower (0.0–0.3) for factual or analytical work, higher for creative tasks
5. Toggle capabilities: web search, vision, MCP tools, memory injection
6. Save

Agents with model overrides allow mixed-model pipelines — for example a fast model for research agents and a more capable model for the synthesis agent in the same workflow run.

Alternatively click **Generate** and describe the agent in plain language — AI fills in the name, role, and system prompt.

---

### Tutorial: Using and Creating Skills

**To enable skills in Compose:** click the **Skills** chip in the Compose input bar — a skill selector opens, showing all available skills as cards. Click a card to toggle it on for this run. The badge on the chip updates to show how many are active.

**To enable skills in Chat:** individual skill chips appear directly in the Chat context bar for enabled chat-scoped skills. Click a chip to toggle it.

**To create a skill manually:** go to **Build → Skills → New skill**. Enter a name, description, scope (All / Chat / Compose), and the instruction text. Write the instruction in second-person imperative: "Always respond with...", "Break every answer into...". Save — the skill is available immediately.

**To generate a skill with AI:**
1. In the Skills panel click **Generate with AI**
2. Describe what you want the skill to do — for example: "Always end responses with three follow-up questions the user should consider"
3. The app uses your configured AI provider and returns a name, description, and instruction prompt
4. The skill editor opens pre-filled — review and save

---

### Tutorial: Running a Task with MCP Tools

Tasks require at least one MCP server connected and an AI provider configured.

1. Connect an MCP server first — go to **Connections** and follow the [MCP tutorial](#tutorial-mcp)
2. Go to **Build → Tasks → New Task**
3. Enter a task name and a goal — describe what you want the LLM to accomplish. The LLM will decide which tools to call and in what order. Example: "Check all open Asana tasks assigned to me and create a summary sorted by due date"
4. Optionally click **Suggest** — AI refines your goal text and references specific tool names from your connected servers
5. Click **Save Task**
6. On the task card, click **Run**

While running the task card shows a pulse-border animation and a live log panel streams each tool call and result. The Tasks nav item shows an "Executing" badge. When the run completes the task card shows the status (OK or ERR), and the result is shown in a collapsible panel.

**From a completed task you can:**
- **Run in Workflow** — pick a workflow from the dropdown on the task card and click Run in Workflow to pass the task result as input to a full agent pipeline
- **Save to Library** — saves the task result as a Library document for future RAG use
- **Make Agent** — creates a pre-configured TOOLS agent with the task goal as its system prompt, for reuse in workflows

**To see run history:** expand the History section on any task card that has been run more than once.

---

### Tutorial: Building Custom Workflows

1. Go to **Build → Workflows → New workflow**
2. Enter a name and description
3. Click **Add agent** to add agents — each becomes a node in the DAG
4. Drag agents to reorder — position determines execution stage. Agents at the same level run in parallel; agents below depend on the stage above. Toggle ⏸ on any agent to enable a HITL checkpoint after it completes
5. Configure workflow-level settings: validation threshold (1–10) and stagger delay between parallel launches
6. Save

Select the workflow in Compose, write a prompt, and press Run. The live DAG executes in stages with parallel agents in each stage running simultaneously.

To generate a workflow from a description: click **Generate** in the Workflows panel, describe the goal, and AI builds a DAG using your existing agents.

---

### Tutorial: Human-in-the-Loop Review

Enable HITL on any agent in the agent editor or in the Workflow Builder.

When the pipeline reaches a HITL agent and it finishes: the pipeline pauses, a review panel shows the agent's output, and three buttons appear — **Approve**, **Edit output**, and **Send feedback**.

- **Approve** — pipeline continues to the next stage immediately
- **Edit output** — edit the agent's output inline before approving
- **Send feedback** — type feedback; it is sent back to the agent as a follow-up instruction; the agent reruns with the feedback; the review panel appears again with the new output

The loop continues until you approve. The pipeline only advances to the next stage after approval.

Enable **Settings → HITL Sound Alert** to play an audio notification when the pipeline pauses, so you do not need to watch the screen.

---

### Tutorial: Installing the Chrome Extension

1. Go to the Nemilia listing on the [Chrome Web Store](https://chromewebstore.google.com/detail/nemilia-ai-workspace/) and click **Add to Chrome**
2. Confirm the permission prompt
3. After installation, click the extension icon in the Chrome toolbar and click **Details**
4. Enable **Allow access to file URLs** — **Crucial:** Chrome disables this by default for security. It must be turned ON for the extension to communicate with Nemilia when opened as a local file.
5. Pin the extension to the toolbar for quick access

---

### Tutorial: Capturing with the Extension

**Text capture:** select text on any page → right-click → **Nemilia → Capture selected text**

**Screenshot:** right-click anywhere → **Nemilia → Capture screenshot** — captures the visible viewport

**Full page:** right-click → **Nemilia → Capture full page** — extracts full readable page content

**Trigger a workflow:** right-click → **Nemilia → Run workflow → [workflow name]** — attaches page content and launches the selected workflow immediately in Nemilia

**Offline queue:** captures made while Nemilia is closed are held in the extension queue and delivered automatically the next time you open the app and log in.

---

### Tutorial: Triaging Captures

Open **Captures** from the sidebar. Each card shows title, source URL, type badge, and processing status badges (BM25, Vector, Vision, RAG Ready).

- Expand a card to preview the content
- Click **Send to Compose** to attach the capture as context for the next workflow run
- Click **Send to Chat** to open a conversation with the capture injected
- Click **Send to Library** to add the content to the RAG library
- Click **Run workflow** to launch a specific workflow with this capture as input
- Use the checkboxes for bulk triage actions

---

### Tutorial: Library and Document RAG

1. Go to **Library → Add document** and select a PDF, DOCX, TXT, or Markdown file
2. The document is chunked, BM25-indexed, and vector-embedded — processing status is shown on the card
3. Toggle the document **Active** to include it in workflow and chat context
4. In Compose or Chat, select documents via the Library/Docs picker in the context bar

**RAG TopK:** go to **Settings → RAG chunk depth** to control how many chunks are retrieved per query. The default is 10. Increase it for large codebases or documents where broader context matters. There is no token cap concern for local models.

To search the Library manually: use the search bar at the top of the Library view — it runs a hybrid BM25 + vector search across all active documents.

---

### Tutorial: Web Search with NEXUS

1. Go to **Connections → Web Search**
2. Select a provider — Serper is recommended for best browser CORS compatibility
3. Paste the API key and save
4. The search pill in the header turns active

In Chat: click the **Web Search** chip in the context bar to enable live search before each message.

In Compose: the search pill in the input bar shows search status. The **NEXUS Search + Synthesis** workflow template uses NEXUS as its first agent to gather live search results before analysis.

**Search providers:**

| Provider | Free tier | Notes |
|----------|-----------|-------|
| Serper | 2,500 queries | Recommended — best browser CORS compatibility |
| Brave | 2,000 queries/month | Requires Data for Search plan |
| Tavily | 1,000 queries/month | AI-optimized results |
| SearXNG | Unlimited | Self-hosted, no API key needed |

---

### Tutorial: Image Generation and Custom Endpoint

1. Go to **Connections → Image Generation**
2. Click a provider card (DALL-E 3, Stable Diffusion, Flux, or Custom)
3. Enter the API key and save

For **Custom**: enter the base URL of any OpenAI-compatible image API, the API key, and save.

Image keys are stored separately from text provider keys. If no image key is set, the app falls back to the active text provider key automatically.

The **VISION agent** generates charts, SVG diagrams, and HTML infographics using the text LLM — no image API key required. Add a VISION agent to any workflow to produce visual outputs alongside prose.

---

### Tutorial: MCP

**Connecting from the Catalog:**
1. Go to **Connections → MCP Servers**
2. The catalog at the top lists available integrations — click **Connect** on any entry
3. The Add Server form opens pre-filled with the server URL, name, and per-service auth guidance
4. Paste your auth token (for services that require one) and click **Save**
5. Transport type (streamable HTTP, SSE, HTTP) is auto-detected before saving
6. Auth tokens go into IndexedDB only — they are never written to `localStorage`

**Adding a custom server:**
1. Click **+ Add custom server**
2. Enter the server name and URL (e.g. `http://localhost:8000/mcp`)
3. Paste a token if required
4. Check **Save as template** to store the name and URL (not the token) as a chip for quick reconnection
5. Click **Test** to verify the connection, then **Save**

**Using the Tool Tester:**
1. In the Tool Tester section below the server list, pick a server from the first dropdown
2. Click **Load tools** if the tool dropdown is empty
3. Pick a tool — the JSON args field auto-populates from the tool's input schema
4. Edit the arguments and click **Run**
5. The output appears below with a pass or fail notification

**Using templates:** saved templates appear as chips below the Add Server form. Click a chip to pre-fill the form with that server's name and URL. Click X on a chip to delete the template.

---

### Tutorial: Memory System

Agents write memories during runs with this exact syntax anywhere in their output:

```
MEMORY[key]: value
```

Example:
```
MEMORY[client_name]: Acme Corp
MEMORY[preferred_format]: executive summary with bullet points
```

**Controlling memory:**
- **Settings → Memory Writes** — allows agents to write new entries (default: off)
- **Settings → Memory Injection** — injects stored memories into agent context (default: off)
- Both are independent — you can inject existing memories without allowing new writes
- The memory chip in the Compose bar reflects the current injection state and can be toggled directly

**Choosing which memories inject:**
1. Go to **Memories** in the sidebar
2. Click **Pick memories**
3. Check only the entries you want injected — leaving all unchecked injects all entries when injection is enabled

To delete an entry: open the Memory panel and click the delete button on its card.

---

### Tutorial: AI Generators

**Generate an Agent:** go to **Build → Agents → Generate** — describe the specialist, AI writes name, role, and system prompt; the agent editor opens pre-filled.

**Generate a Prompt:** go to **Build → Prompts → Generate** — describe what the prompt should accomplish; AI writes the full template with `{{variable}}` placeholders; the prompt editor opens pre-filled.

**Generate a Workflow:** go to **Build → Workflows → Generate** — describe the goal; AI builds a DAG using your existing agents; opens in the workflow editor.

**Generate a Task:** go to **Build → Tasks → Generate** — describe the goal; AI writes a task name and goal referencing your connected tool names; the task editor opens pre-filled.

**Generate a Skill:** in **Build → Skills**, click **Generate with AI** — describe the behavior; AI writes the instruction prompt; the skill editor opens pre-filled.

---

### Tutorial: Running Local Models

**Ollama:**
1. Install from [ollama.com](https://ollama.com) and start it
2. Pull a model: `ollama pull llama3.2`
3. In Nemilia open the provider modal, select **Ollama**, and save — model is detected automatically

**LM Studio:**
1. Install from [lmstudio.ai](https://lmstudio.ai), load a model, and start the local server (Server tab)
2. In Nemilia select **LM Studio** — the active model and context window length are auto-detected

**Jan:**
1. Install from [jan.ai](https://jan.ai), load a model, and enable the local API server
2. In Nemilia select **Jan** — active model is auto-detected

**Llamafile:**
1. Download a `.llamafile` from [Mozilla's repository](https://github.com/Mozilla-Ocho/llamafile), make it executable, and run it — it starts on port 8080
2. In Nemilia select **Llamafile** — active model is auto-detected

---

### Tutorial: Running In-Browser Models

**WebLLM:**
1. Open the provider modal and select **Browser (WebLLM)** from the Local tab
2. The model grid shows available models with their VRAM requirement — **Qwen 2.5 7B (5.1 GB)** is recommended
3. Click **Load model** — downloads once and caches in the browser; a progress ring tracks the download
4. Once loaded the provider pill turns active — inference runs entirely in your browser GPU

Switching to another provider unloads the engine automatically to free GPU memory.

**Chrome AI (Gemini Nano):**
1. Open Chrome 127+ desktop
2. Go to `chrome://flags/#prompt-api-for-gemini-nano`, set it to **Enabled**, and relaunch Chrome
3. In Nemilia select **Chrome AI (Gemini Nano)** — no download; Nano is already in Chrome
4. Save

Chrome AI is suitable for direct chat. It does not support the full workflow pipeline.

---

### Tutorial: Connecting a Custom API Provider

1. Open the provider modal and select **Custom API**
2. Enter the base URL of the endpoint (e.g. `https://your-host.com/v1/chat/completions`)
3. Enter a display name and the model ID the endpoint expects
4. Paste your API key if required
5. Save

The endpoint must return `Access-Control-Allow-Origin` CORS headers, or the browser will block requests. For local self-hosted endpoints this is not an issue. For remote endpoints, configure CORS on the server side or use the Nemilia Chrome extension, which relays requests.

---

### Tutorial: Workspace and File Management

**Connecting a local folder:**
1. Go to **Settings → Storage → Connect folder**
2. A system folder picker opens — choose or create a folder
3. Click **Allow** when prompted for permission
4. Nemilia syncs your workspace to disk on every save

Once connected, workspace files are accessible in any text editor. The storage mode indicator in Settings shows **File System** when active.

**Storage fallback order:**
1. File System API (Chrome and Edge only) — workspace folder on disk
2. IndexedDB — persists across sessions, no practical size limit for typical workspaces
3. `localStorage` — fallback only, approximately 5 MB limit

If storage is full Nemilia shows a notification and strips document chunk data from the save to reduce size. Clear old results or chat history to free space.

---

## Provider Reference

### Provider API

| Provider | Notes |
|----------|-------|
| Groq | Fastest inference; large free tier; Llama 4, DeepSeek R1, Kimi K2, Qwen 3 |
| OpenAI | GPT-4.1, o3, o4-mini |
| Anthropic | Claude Opus 4.7, Sonnet 4.6, Haiku 4.5 — prompt caching enabled |
| Google Gemini | Gemini 2.5 Pro and Flash; generous free tier |
| OpenRouter | 200+ models including free tier; meta-routing |
| Mistral | Mistral Large, Codestral |
| DeepSeek | DeepSeek V3, R1 |
| xAI Grok | Grok 3, Grok 3 mini |
| Kimi (Moonshot) | Kimi K2 1T MoE; long context |
| Fireworks AI | DeepSeek V4 Pro, Kimi K2.6, Qwen 3.6 Plus, GLM 5.1; 17 serverless models |
| Perplexity | Sonar, Sonar Pro, Sonar Reasoning — built-in live web search |

### Local Server

| App | Port | Notes |
|-----|------|-------|
| Ollama | 11434 | Any pulled model; no key; auto-detect |
| LM Studio | 1234 | Any loaded model; native API gives context window metadata |
| Jan | 1337 | Cross-platform; any loaded model |
| Llamafile | 8080 | Mozilla; single-file executable |

### In-Browser

| Mode | Requirement |
|------|-------------|
| WebLLM (Browser / WebGPU) | Chrome 121+ or Edge 121+ with hardware acceleration enabled |
| Chrome AI (Gemini Nano) | Chrome 127+ desktop; `chrome://flags/#prompt-api-for-gemini-nano` enabled |

---

## Architecture

### Single-File Design

The entire application is one `.html` file. No build step, no bundler, no framework.

| Library | Version | Bundled as |
|---------|---------|-----------|
| PDF.js (Mozilla) | 3.11.174 | Inlined — main library and worker both embedded; CDN fallback fires only if inline fails |
| DOMPurify | 3.1.5 | Inlined — XSS sanitization of all rendered output |
| Chart.js | 4.4.1 | Inlined — chart rendering for VISION agent output |
| Transformers.js (Xenova) | 2.17.2 | Fetched from CDN on first document or capture embedding; `all-MiniLM-L6-v2` model weights downloaded once and browser-cached |
| WebLLM (MLC AI) | 0.2.81 | Fetched from CDN when the WebLLM provider is first selected; model weights downloaded once and browser-cached |

PDF.js, DOMPurify, and Chart.js are fully self-contained — no network request required to use them. Transformers.js and WebLLM fetch from CDN the first time they are needed; every subsequent use is served from the browser cache.

### Storage Architecture

```
Three-tier storage (automatic fallback):
  File System API (Chrome/Edge) → IndexedDB → localStorage
```

All workspace data is encrypted per profile before being written to any storage tier. Document chunks and vector embeddings live in IndexedDB. When a File System folder is connected the workspace is additionally synced to disk on every save.

---

## Security and Privacy

- Workspace encrypted at rest: AES-256-GCM, key derived via PBKDF2 (200,000 SHA-256 iterations) from your profile password
- MCP auth tokens stored in IndexedDB only — never serialized to `localStorage`
- API keys stored per-profile in a scoped key store — inaccessible to other profiles
- On logout, all in-memory workspace data is explicitly zeroed before the login overlay appears
- DOMPurify 3.1.5 sanitizes all HTML rendered from workflow and agent output
- Zero telemetry — no analytics, no tracking, no beacons
- CSP `connect-src` locked to an explicit allowlist of known provider endpoints

**What leaves your browser** (only when you explicitly initiate it):
- LLM API calls to your configured provider
- Search API calls when web search is triggered
- Image API calls when image generation is used
- Transformers.js library and `all-MiniLM-L6-v2` model weights on first document or capture embedding (browser-cached after)
- WebLLM library and selected model weights on first WebLLM use (browser-cached after)

---

## Browser Compatibility

| Browser | Version | Notes |
|---------|---------|-------|
| Chrome | 121+ | Full support — recommended; File System API, extension, WebLLM |
| Edge | 121+ | Full support including File System API and WebLLM |
| Safari | 17+ | Full support; File System API limited |
| Firefox | 120+ | Full support; no File System API; no WebLLM |

WebLLM requires Chrome 121+ or Edge 121+ with hardware acceleration enabled. Chrome AI requires Chrome 127+ desktop with the flag enabled.

---

## Settings Reference

| Setting | Default | Description |
|---------|---------|-------------|
| System prompt | — | Default system prompt for all agents when no agent-level override is set |
| Max output tokens | 32,768 | Upper ceiling for model responses |
| Temperature | 0.7 | Global default (0.0–1.0) |
| Max retries | 3 | Auto-retry attempts per agent on validation failure |
| DAG stagger delay | 600 ms | Delay between parallel agent launches within the same stage |
| RAG chunk depth (TopK) | 10 | Chunks retrieved per query; increase for large codebases |
| Captures preview length | 400 chars | Characters shown in the expanded capture card preview |
| Show Dashboard after login | ON | Whether the Dashboard opens after login instead of Compose |
| HITL Sound Alert | — | Audio notification when the pipeline pauses for review |
| Reasoning tags — Chat | ON | Render `<think>` blocks as a collapsible badge in Chat |
| Reasoning tags — Compose | ON | Render `<think>` blocks as a collapsible badge in Compose |
| Memory Writes | OFF | Allow agents to write new memories during runs |
| Memory Injection | OFF | Inject stored memories into agent context |
| Cost Tracking | — | Show estimated cost during runs; configure cost per 1K tokens |
| Orchestrator planning temp | 0.2 | Temperature for the Orchestrator's planning pass |
| Orchestrator synthesis temp | 0.2 | Temperature for the Orchestrator's synthesis pass |
| Orchestrator validation threshold | 6 | Minimum score (1–10) before agent output is accepted |
| Storage | — | Live usage breakdown across File System / IndexedDB / localStorage |
| Browser Compatibility | — | Runtime compatibility check for current browser |
| Hardware | — | GPU, VRAM, and RAM detection for WebLLM model selection |

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Send chat message / send follow-up |
| `Shift + Enter` | New line in chat or follow-up input |
| `Ctrl/Cmd + K` | Focus the Compose input from anywhere (does not fire if already inside an input or textarea) |
| `Escape` | Close modal |
| `Tab / Shift + Tab` | Cycle focus within an open modal (focus trapped inside) |

---

## What's New in v2.2

**Drag-and-Drop File Attach (Chat + Compose)** — drop PDF, DOCX, TXT, Markdown, code, CSV, JSON, YAML, or image files anywhere on the Chat or Compose surface. Dropped files are added to the Library (full parse → chunk → embed → IDB pipeline) AND auto-attached as context for the current session. A large blurred overlay with an animated download glyph appears on drag-enter, pulses green on successful drop, and reports "N files added to Library · attached to chat/Compose" via toast. Pop-out Chat inherits the same drop zone automatically. Strict file-type allowlist — unsupported files are rejected with an actionable warning toast rather than silently failing.

**Clipboard Paste Attach** — paste images or files (Ctrl+V / Cmd+V) directly into the chat or compose input. Same ingest pipeline as drag-drop. Clipboard images arriving as generic `image.png` are auto-renamed to `pasted-<timestamp>.png` for traceability. Normal text paste continues to work untouched when the clipboard has no files.

**Paperclip Attach Button** — a 📎 button sits to the left of the chat and compose textareas for click-to-attach (multi-select). Uses the same strict allowlist as drag-drop and the same ingest pipeline — identical behavior whether you drop, paste, or click.

**Streaming Status Badge** — every streaming assistant message now displays a live-ticking badge that transitions through **Working… → Generating… → Responded in Ns** for standard models, or **Thinking… → Thought for Ns** for reasoning models (DeepSeek R1, Qwen QwQ, OpenRouter reasoning streams). Applied uniformly across main chat, pop-out chat, chat synthesis rounds (after MCP tool calls), workflow follow-up, compose direct, compose MCP tool loops, and compose follow-up. Elapsed time ticks every second during streaming and freezes at the final value when the response completes or is stopped. Stop button preserves the badge state at abort time.

**Markdown Rendering Upgrades** — the inline markdown renderer (`mdToHtml`) now handles:
- **GFM pipe tables** with per-column alignment (`:---`, `:---:`, `---:`) and alternating-row striping
- **Task lists** — `- [ ] item` and `- [x] done` render as checkboxes with strikethrough on checked items
- **Strikethrough** — `~~text~~` renders as `<del>`
- **h4–h6** headers (previously only h1–h3)
- **Streaming-safe code fences** — partial fenced code blocks render inside `<pre>` during streaming rather than breaking mid-stream; the temporary close closes cleanly when the real close arrives
- **Language class on fences** — `<pre><code class="language-python">…</code></pre>` preserves the language hint on every fenced block, ready for future syntax highlighting (hljs / Prism) without further code changes
- All upgrades apply to chat messages, workflow output, compose direct, and the collapsible reasoning badge content

**Multi-Profile Encrypted Workspace** — create multiple isolated profiles, each with its own encrypted workspace. Encryption uses PBKDF2 (200,000 SHA-256 iterations) + AES-256-GCM on your password. Recovery codes generated at creation. MCP tokens moved to IndexedDB, never `localStorage`. API keys scoped per profile, zeroed on logout.

**Dashboard** — post-login home screen with live workspace stats, provider status, quick-action tiles, and recent activity. Provider pill stays in sync without page reload.

**Skills System** — ten built-in skills (all off by default) covering tone, format, and analytical stance, each scoped to All, Chat, or Compose. Manual skill editor and an AI generator that uses your configured provider to write the instruction prompt.

**AI Generators** — generate Agents, Prompts, Workflows, Tasks, and Skills from a plain-language description. Task generator references your connected MCP tool names.

**Sidebar Profile Row** — avatar, display name, and action icon; click to log out or switch profiles.

**Tasks** — autonomous LLM + MCP tool execution. Each task has a name and goal; the agent calls tools in a loop, logs each call live, and stores a full run history. Run in Workflow, Save to Library, and Make Agent actions on each completed task.

**MCP Catalog** — curated integrations with pre-filled connection details and per-service auth guidance. Auth field hidden for no-auth servers.

**MCP Tool Tester** — test any tool from any connected server directly in the Connections panel. JSON args auto-populated from tool schema.

**MCP Saved Templates** — save server name and URL (never token) as chips for quick reconnection.

**Friendly Error Messages** — all API errors translated to plain-language descriptions with actionable guidance instead of raw error strings.

**Thinking Tag Overhaul** — Qwen-style `/think`, `/no_think`, `/thinking` prefix tokens stripped before tag processing. OpenRouter reasoning models (Qwen3, DeepSeek-R1) that stream in `delta.reasoning_content` are now wrapped in `<think>` tags and rendered as the collapsible reasoning badge.

**Memory Improvements** — writes and injection both default to off. Pick Memories button selects exactly which entries inject. Memory chip in Compose bar reflects and toggles injection state.

**Custom Image Endpoint** — any OpenAI-compatible image API can be connected. Image keys stored separately from text provider keys with automatic fallback.

**Max Tokens Default** — raised from 8,192 to 32,768.

**RAG TopK Setting** — user-configurable chunk depth; default 10.

**Chrome Web Store Extension** — install from Chrome Web Store; manual zip install removed.

**Gemini Token Cap Fix** — `maxOutputTokens` guarded to fall back to 8,192 when calculated value is zero.

**Anthropic Model Refresh Fix** — `anthropic-dangerous-direct-browser-access: true` header added to the model refresh call.

**Settings Close Button** — explicit close button added to the Settings panel header.

**Mobile-Responsive Overhaul** — iOS safe area insets, bottom-sheet modals at 480px, dashboard 3-column grid on phones, chat sidebar collapses horizontally at 600px, touch-action set on all interactive elements, single-column provider and model grids at 540px, login card bottom-sheet on small phones.

**Focus Trap for Modals** — Tab and Shift+Tab cycle within open modals. Escape closes and releases.

**Ctrl+K / Cmd+K** — focuses the Compose input from anywhere in the app.

**Task Running Animation** — pulse-border animation on running tasks; collapsible execution log per task card; running badge on the Tasks nav item.

**DOMPurify 3.1.5 Inlined** — full library inlined for XSS sanitization of all rendered workflow, agent, and task HTML output.

**Compose Bar Memory Chip** — syncs with the memory injection toggle; click to toggle directly from Compose.

**Vision Queue Progress Bar** — color corrected from amber to teal for consistency with the embed queue.

---

## License

Business Source License 1.1 (BSL 1.1)

Source-available — free for personal and non-commercial use.

- **Licensed Work:** Nemilia AI Workspace v2.2
- **Licensor:** Luis Lopez / Nemilia AI
- **Change Date:** 2030-02-27
- **Change License:** MIT

On the Change Date the license automatically converts to MIT. Full BSL 1.1 text: [mariadb.com/bsl11](https://mariadb.com/bsl11/)

For commercial licensing: [luis@nemilia.com](mailto:luis@nemilia.com)
