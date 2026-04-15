# Use Cases (what you can do, and why Smart AI asks for setup)

Smart AI is designed for **live operations**, not just document Q&A. That’s why the setup focuses on:

- Connecting a **Smart Functions repository** (your approved tool catalog)
- Defining **Meta** (inputs/outputs) so tools are callable
- Creating **connections + credentials** so tools run against real systems
- Using **tags/domains/collections** to keep the catalog consistent at scale

Below are common use cases written in a “why + how” style (similar to modern developer docs).

---

## Order detail / status lookup (single system)

### What you’re trying to do
Answer a question like: “Show me details of order `12345`.”

### Why Smart AI helps
Instead of navigating multiple screens, users ask in natural language and Smart AI runs the approved order lookup tool.

### What you need (setup)
- An approved function like `get_order_details` or `get_order_status`
- A working connection for the right environment (Dev/QA/Prod)

### Example prompts
- “Show me details of order 12345.”
- “What is the current status and last update time?”
- “Only show lines that are backordered.”

---

## Cross-system order visibility (Enterprise Mesh)

### What you’re trying to do
Get a single trusted answer when data is split across systems:

- ERP has the commercial status
- WMS has pick/pack/ship progress
- TMS has tracking events

### Why Smart AI helps
Enterprise Mesh can query multiple systems in parallel and merge results into a single response, using your organization’s approved precedence rules.

### What you need (setup)
- Approved cross-system functions (for example, “unified order status”)
- Connections and credentials for each participating system

### Example prompts
- “Check order 12345 across the enterprise”
- “Show delayed orders for system A and B”
- “Which system is the source of the current status?” (if transparency is enabled)

---

## Inventory check (with follow-ups)

### What you’re trying to do
Ask “How many units of SKU `ABC` are in Warehouse `5`?” and then refine.

### Why Smart AI helps
Users can start broad, then narrow without running separate reports:

- Filter, group, and summarize the last dataset
- Turn it into charts and dashboards

### Example prompts
- “How many units of SKU ABC are in Warehouse 5?”
- “Group by location type.”
- “Only show low-stock locations.”
- “Create a bar chart by zone.”

---

## Operational lookups (areas, devices, work items)

### What you’re trying to do
Quickly retrieve operational entities that normally take multiple screens.

### Example prompts
- “Show me area information for Building X.”
- “Give me a list of all devices.”
- “Show open work items for user jsmith.”

---

## Analytics, charts, dashboards, and transparency

### What you’re trying to do
Turn a dataset into something decision-ready.

### Why Smart AI helps
Once a tool returns a table/dataset, Smart AI can:

- Create charts (pie/line/bar/stacked/bubble, based on availability)
- Generate an interactive dashboard
- Explain what it executed behind the scenes (when enabled)

### Example prompts
- “Create a pie chart from this.”
- “Show a time-series chart by ship date.”
- “Build a dashboard for this dataset.”
- “What did you do?”

---

## Use Smart AI tools inside other clients (MCP)

### What you’re trying to do
Use the same governed enterprise tools from a different AI client (for example, Claude Desktop).

### Why Smart AI helps
MCP exposes a curated tool catalog for a project/system so external clients can discover and call approved functions.

### What you need (setup)
- Tools tested in Dev Console
- Connections + credentials configured
- An MCP server generated for the correct project/system

See:

- [MCP (Model Context Protocol)](./mcp.md)

