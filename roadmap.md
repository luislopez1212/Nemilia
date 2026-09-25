Nemilia AI Workspace — Product Roadmap
Updated September 2026


v2.3 — Nemilia Drives the Web

Theme: Nemilia agents operate the websites you already have open, through the tools those sites publish. The app stays a single local file. Nothing is hosted, nothing leaves the browser.

WebMCP Tab Bridge
WebMCP is the W3C proposal (Chrome origin trial since Chrome 149) that lets a website publish structured tools such as search_flights or add_to_cart to browser agents. The Nemilia extension now discovers those tools in every open tab and makes them available to your agents. An agent in chat or in a workflow can call a tool on a site you have open, and the site executes it with your live session, cookies, and state.

Tools are discovered when a tab finishes loading and rediscovered after every execution, since sites can change or remove tools as you navigate. Discovery is read-only. Execution only happens when an agent you are running calls a tool.

Requires the Nemilia extension v2.3.0 and a Chromium browser with WebMCP available. Chrome 149 or later with the WebMCP flag enabled, or the origin trial on the site's side. Sites using the WebMCP polyfill work in any Chrome.

WebMCP Chip in Chat
A separate chip next to the MCP chip, off by default. Turn it on and the current chat can see tools from open tabs. Workflow agents get a matching per-agent setting, so a workflow can use remote MCP servers without exposing tab tools, or the reverse. The chip shows which tabs contributed tools and how many.

Tool Execution Policy
Every tool call, whether from a remote MCP server or a WebMCP tab, passes through one policy layer:
- Tools marked consequential by the site (booking, purchasing, deleting) require your confirmation in chat. In workflows, a per-workflow setting chooses between pausing for approval or allowing the call. New workflows default to pause.
- Tool output marked as untrusted by the site is delimited as data before it reaches the model, so page content cannot issue instructions to your agent.
- Read-only tools are distinguished from tools that change state, and agents restricted to read-only cannot call the latter.
- Per-call timeouts and a hard cap on tool rounds per turn.

Execution stays on the Nemilia tab. The browser does not switch to the target site while a tool runs.

Tool Audit Log
Every tool execution is recorded: source (remote server or tab), tool name, arguments, result, agent, run, timestamp, and the WebMCP API generation detected in the browser. Entries are encrypted with the active profile key. When no profile is unlocked, only metadata and content hashes are stored. Exportable as JSON from Settings.

Nemilia as a WebMCP Provider
When Nemilia runs on a secure origin, it registers its own tools (run_workflow, quick_capture, search_library, compose) so browser agents such as Gemini in Chrome can drive Nemilia. On the default local file this code never activates and has no effect. It exists so an organization that chooses to host Nemilia on its own origin gets the capability without a separate build.

Adaptive Context
Before running RAG retrieval, Nemilia checks whether your selected documents fit in the model's context window using the per-model measurements introduced in v2.2. If they fit, they are sent directly instead of chunked and retrieved. The run log shows when this path was taken.

Extension v2.3.0
Adds the WebMCP bridge. No new permissions. Compatible with app v2.2. The README privacy section is updated to describe tab scanning.


v2.3.1 — Follow-up

Native Tool Calling for Cloud Providers
v2.2 uses native function-calling parameters for local providers (LM Studio, Ollama, Jan, WebGPU) and text parsing for everything else. This extends native tool calls to cloud providers, with text parsing kept as the fallback. WebMCP tools carry strict JSON schemas, and native calls parse them far more reliably.

Export Any Message
Every assistant reply gets an export control that opens a clean preview and downloads as Markdown or PDF. When a reply is a complete document, it surfaces as a Document ready chip with the same preview.


v2.4 — Agents That Plan

Unified Agent Loop
One execution engine shared by chat and workflow nodes, replacing the separate chat loop and single-pass workflow tool execution.

Autonomous Agent Loops (ReAct)
Workflow agents that think, act, observe the result, and decide the next step until the goal is met. Built on the unified loop and the policy layer from v2.3.

Workflow Run Evaluation
Compare outputs across runs with the same prompt and different models or configurations. Fed by the audit log.

Scoped Workspace Storage
Saves write only what changed instead of the entire workspace, with per-collection stores. Meaningful at 100+ chats or 200+ captures. Includes a one-time migration.

Background Embedding
The embedding pipeline moves off the main thread so indexing large captures does not compete with the UI.


Under Consideration
- WebMCP declarative tools: Nemilia's own forms annotated as tools for the hosted case
- Memory relevance weighting


Compatibility Note
WebMCP is an origin trial and the API has changed several times in 2026. All contact with the browser API is isolated in the extension so that changes ship as extension updates without a new app build. The Connections panel shows which API generation was detected.

Features are ordered by expected delivery within each release.
