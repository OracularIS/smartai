# Use Cases
---

## Smart FX Studio

Create, maintain and validate enterprise smart functions with standardized schemas, secure system connections, automated reliability testing, and full debugging capabilities to power consistent AI operations across your organization.

```text
- Create a new function to look up shipment tracking status
- Update the order schema to include new delivery priority field
- Run evaluation test suite after updating inventory functions
- Add new database connection for production environment
- View debug trace for failed function execution
```

---

## Enterprise Mesh
Secure real-time federated execution layer that unifies your enterprise systems, enabling parallel queries, atomic cross-system workflows with automatic rollback, and complete audit tracking—all while keeping business data within your network. Gain unified answers and execute operations seamlessly across platforms without data replication.

```text
- Show me the complete status for order 12345 across all systems
- What is the total available inventory for SKU ABC including in-transit?
- Which system is the source of this status value?
- Fulfill this order end to end across ERP, WMS and TMS
- Update this customer's contact details everywhere
- Show me exactly what steps will run if I cancel this order
- Retry all failed operations from yesterday's batch
```

---

## Unified Operational Data Lookup

Access orders, inventory, and operational data through a single natural language interface—eliminating the need to navigate multiple systems or screens. Retrieve detailed insights, filter results dynamically, and drill down into exceptions or trends in real time. This enables faster decision-making and a seamless workflow across enterprise operations.

```text
- Show me details of order 12345 and highlight any delays.
- How many units of SKU ABC are available across all warehouses?
- List all low-stock locations grouped by warehouse.
- Show open work items assigned to user jsmith.
- Give me device status across Building X.
```

---

## Analytics, charts and dashboards

Transform raw operational data into actionable insights with automatic chart generation, interactive dashboards, and full transparency over executed operations. Export results in multiple formats to support reporting and decision workflows.

```text
- Show order volume per hour for the last 12 hours as a line chart across all warehouses.
- Break down current on-hand inventory by zone and building as a stacked bar chart.
- Build a live dashboard showing today's picking productivity by user shift.
- Show me exactly which systems were queried and what functions executed for this result.
```

---

## Execute actions & update systems

Execute approved operations and modify live system data securely using natural language, with full governance, audit logging, permission controls, optional approval workflows, and safe simulation mode for testing changes before production execution.

```text
- Cancel order 12345 and send notification to customer
- Adjust SKU ABC in warehouse 5 by +25 units
- Assign work order 789 to user jsmith
- Run daily inventory reconciliation for location west
- Simulate cancelling order 4567 first before doing it for real
```

---

## Use tools inside other clients (MCP)

Use your approved enterprise tools directly inside other AI clients.

- Works with Claude, Cursor, VS Code and any MCP compatible assistant
- All governance, permissions and connections work exactly the same way
- No extra setup required per tool
- Safe discovery of only approved functions