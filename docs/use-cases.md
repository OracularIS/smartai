# Use Cases

Smart AI is designed for **live operations**, not just document Q&A. Below are the most common things you can do.

---

## Order detail / status lookup

Look up order information using natural language, instead of navigating multiple application screens.

- Get full order details, status and timeline
- Filter for specific items, backorders or exceptions
- See exactly when and where changes happened

**Example prompts:**
- "Show me details of order 12345."
- "What is the current status and last update time?"
- "Only show lines that are backordered."

---

## Inventory check

Query inventory levels and work with the results without running separate reports.

- Check stock counts by SKU, location or warehouse
- Filter, group and summarise results
- Narrow down results with follow up questions
- Generate charts directly from the dataset

**Example prompts:**
- "How many units of SKU ABC are in Warehouse 5?"
- "Group by location type."
- "Only show low-stock locations."
- "Create a bar chart by zone."

---

## Operational lookups

Quickly retrieve operational entities that normally take multiple steps to find.

- Area and location information
- Device status and lists
- Work items assigned to users or teams
- Production line status and metrics

**Example prompts:**
- "Show me area information for Building X."
- "Give me a list of all devices."
- "Show open work items for user jsmith."

---

## Analytics, charts and dashboards

Turn raw datasets into something decision ready.

- Generate standard chart types automatically
- Build interactive dashboards
- See transparency about exactly what was run
- Export data in different formats

**Example prompts:**
- "Create a pie chart from this."
- "Show a time-series chart by ship date."
- "Build a dashboard for this dataset."
- "What did you do?"

---

## Execute actions & update systems

Actually change data in live systems, not just read it.

- Run approved operations using natural language
- Full governance, audit logging and permission checks
- Optional approval gates for sensitive operations
- Dry run / simulation mode for testing changes

**Example prompts:**
- "Cancel order 12345 and send notification to customer"
- "Adjust SKU ABC in warehouse 5 by +25 units"
- "Assign work order 789 to user jsmith"
- "Run daily inventory reconciliation for location west"
- "Simulate cancelling order 4567 first before doing it for real"

---

## Smart FX Studio

Create, maintain and validate the smart functions that power Smart AI operations.

- Define and update function metadata and implementations
- Standardize vocabulary and schemas across your entire organization
- Manage secure connections to external systems
- Validate tool calling reliability with automated evaluations
- Troubleshoot and debug function execution behaviour

**Example workflows:**
- "Create a new function to look up shipment tracking status"
- "Update the order schema to include new delivery priority field"
- "Run evaluation test suite after updating inventory functions"
- "Add new database connection for production environment"
- "View debug trace for failed function execution"

---

## Enterprise Mesh (Cross system operations)

Real-time federated execution layer that connects all your enterprise systems securely.

- Query multiple systems in parallel without data replication
- Get single unified answers when information exists in different places
- Calculate real-time available-to-promise inventory across all locations
- Run end to end workflows that update multiple systems atomically
- Automatic rollback if any step in a multi-system operation fails
- Enforce consistent RBAC permissions across all integrations
- Full audit trail, provenance and execution tracking for every value
- Zero raw business data leaves your internal network

**Example prompts:**
- "Show me the complete status for order 12345 across all systems"
- "What is the total available inventory for SKU ABC including in-transit?"
- "Which system is the source of this status value?"
- "Fulfill this order end to end across ERP, WMS and TMS"
- "Update this customer's contact details everywhere"
- "Show me exactly what steps will run if I cancel this order"
- "Retry all failed operations from yesterday's batch"

---

## Use tools inside other clients (MCP)

Use your approved enterprise tools directly inside other AI clients.

- Works with Claude Desktop, Cursor, VS Code and any MCP compatible assistant
- All governance, permissions and connections work exactly the same way
- No extra setup required per tool
- Safe discovery of only approved functions