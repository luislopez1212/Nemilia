Nemilia v2.3 — Product Roadmap


Agents Can Now Use Your Tools
Agents in Workflow Builder can autonomously call MCP tools during execution — searching, fetching, writing, querying — without you wiring each step manually. You describe the goal; the agent decides which tools to invoke and when.

This is the biggest unlock for complex, multi-step workflows where the path to a result isn't linear.

Document & Export
Artifact Mode — Documents That Know They're Documents
When a model generates a complete document (report, proposal, structured data), Nemilia now recognizes it as a document rather than a chat reply. It surfaces as a "Document ready" chip in the conversation, opening a full preview with one-click export to PDF or Markdown.

No copy-pasting. No "save as." The output comes out as a file.

Export Any Message
Every assistant reply gets a lightweight export button. Click it to open the message in a clean preview and download as PDF or Markdown — whether it was detected as a document or not. Designed for when you want to grab a single reply without saving a full Library item.

Both features share the same preview modal and use the browser's native PDF engine — no external dependencies, no file size limits.

Performance & Scale
Embedding Runs in the Background
The embedding pipeline moves off the main thread. Indexing large captures or running embed queues no longer competes with the UI — the app stays responsive while processing happens quietly in the background.

Smarter Storage at Scale
Workspace saves are now scoped to what changed rather than rewriting the entire workspace on every update. Meaningful at 100+ chats or 200+ captures — saves are faster and less likely to hit browser storage limits under heavy use.

Adaptive Context — Skip Retrieval When It's Not Needed
Before running RAG retrieval, Nemilia now checks whether your selected documents simply fit in the model's context window. If they do, it sends them directly instead of chunking and retrieving. Faster responses, fewer retrieval misses on small doc sets.

Agent Intelligence
Autonomous Agent Loops (ReAct)
Today's workflow execution follows a fixed DAG — each node runs in a defined order. ReAct agents think, act, observe the result, then decide what to do next — repeating until the goal is met. Enables genuinely open-ended tasks where the steps can't be specified upfront.

Workflow Run Evaluation
Compare outputs across workflow runs — same prompt, different models or configurations. Identify which setup produces better results without running blind A/B comparisons by hand.

Under Consideration
Web MCP — browser-accessible MCP server connections without a local proxy
Structured output mode — use native function-calling parameters for more reliable tool parsing, with regex as fallback
Memory relevance weighting — memories ranked by recency and usage frequency rather than flat key-value storage
Features are ordered by expected delivery priority within v2.3. Items under consideration are planned but not yet scoped.

