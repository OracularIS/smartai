# Use Cases (what you can do, and why Smart AI asks for setup)

Smart AI is designed for **live operations**, not just document Q&A. That’s why the setup focuses on:

- Connecting a **Smart Functions repository** (your approved tool catalog)
- Defining **Meta** (inputs/outputs) so tools are callable
- Creating **connections + credentials** so tools run against real systems
- Using **tags/domains/collections** to keep the catalog consistent at scale

Below are common use cases written in a “why + how” style (similar to modern developer docs).

---

## Order detail / status lookup (single system)

### What this does
Answer a question like: “Show me details of order `12345`.”

### Why this is better
Instead of navigating multiple screens, users ask in natural language and Smart AI runs the approved order lookup tool.

### What you need (setup)
- An approved function like `get_order_details` or `get_order_status`
- A working connection for the right environment (Dev/QA/Prod)

### Example prompts
- “Show me details of order 12345.”
- “What is the current status and last update time?”
- “Only show lines that are backordered.”

---

## Inventory check (with follow-ups)

### What this does
Ask “How many units of SKU `ABC` are in Warehouse `5`?” and then refine.

### Why this is better
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

### What this does
Quickly retrieve operational entities that normally take multiple screens.

### Example prompts
- “Show me area information for Building X.”
- “Give me a list of all devices.”
- “Show open work items for user jsmith.”

---

## Analytics, charts, dashboards, and transparency

### What this does
Turn a dataset into something decision-ready.

### Why this is better
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

## Execute actions & update systems (Smart FX)

### What this does
Actually change data in live systems, not just read it. Safely run approved operations using natural language.

### Why this is better
No more opening 5 different screens to perform standard operations. All actions run through your approved functions with full governance, audit logging and permission checks enforced automatically.

### What you need (setup)
- Approved write/action functions with defined input schemas
- Execution permissions configured for user roles
- Optional approval gates configured for sensitive operations
- Dry run / simulation mode enabled for testing

### Example prompts
- "Cancel order 12345 and send notification to customer"
- "Adjust SKU ABC in warehouse 5 by +25 units"
- "Assign work order 789 to user jsmith"
- "Run daily inventory reconciliation for location west"
- "Simulate cancelling order 4567 first before doing it for real"

---

## Enterprise Mesh (Cross system operations)

### What this does
Single source of truth across all your systems. Query data across platforms, run multi-step workflows, and safely execute distributed operations with guaranteed consistency.

This handles both:
**Unified visibility** - get one trusted answer when data exists in multiple places
**Orchestrated actions** - run end to end workflows that update multiple systems

Systems are never out of sync. If any step fails, everything automatically rolls back cleanly.

### Why this is better
No more checking 3 different screens for an order status. No more manually updating 5 systems and hoping you don't miss one.

Enterprise Mesh:
- Queries multiple systems in parallel
- Merges results using your company's precedence rules
- Runs entire transactional workflows
- Automatically rolls back on failure
- Maintains full audit trail for every operation
- Shows you exactly which system provided each value

### What you need (setup)
- Approved cross-system functions and workflow definitions
- Connections and credentials for each participating system
- Transaction boundaries and rollback rules defined
- Optional fallback systems configured for high availability

### Example prompts
- "Show me the complete status for order 12345 across all systems"
- "Which system is the source of this status value?"
- "Fulfill this order end to end"
- "Update this customer's contact details everywhere"
- "Show me exactly what steps will run if I cancel this order"
- "Retry all failed operations from yesterday's batch"

---

## Bulk operations & batch processing

### What this does
Run operations across hundreds or thousands of records consistently.

### Why this is better
No more spreadsheet uploads, manual data entry or writing one-off scripts. Apply the same action to an entire filtered dataset with full validation and progress tracking.

### Example prompts
- "Mark all orders older than 90 days as completed"
- "Update delivery date for all orders on this shipment"
- "Send reminder notifications to all users with open work items"
- "Export this entire filtered list as CSV"

---

## Exception handling & alert resolution

### What this does
Respond to operational alerts and resolve common issues automatically.

### Why this is better
Instead of just notifying you that something is broken, Smart AI can investigate the problem, run diagnostic tools, apply standard fixes and confirm resolution - all from the alert notification.

### Example prompts
- "This order is stuck, check what's wrong and fix it"
- "Resolve the inventory discrepancy for SKU XYZ"
- "Restart the failed import job"
- "Apply the standard workaround for error 5002"

---

## Use Smart AI tools inside other clients (MCP)

### What this does
Use your approved enterprise tools directly inside other AI clients like Claude Desktop, Cursor, VS Code or any MCP-compatible assistant. All your existing governance, permissions and connections work exactly the same way.

### Why this is better
Smart AI automatically exposes your curated tool catalog through MCP, so external clients can safely discover and call only your approved functions - no extra setup required per tool.

### What you need (setup)
- Tools tested in Dev Console
- Connections + credentials configured
- An MCP server generated for the correct project/system

See:

- [MCP (Model Context Protocol)](./mcp.md)