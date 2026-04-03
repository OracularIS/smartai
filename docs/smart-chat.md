# Smart Chat

Smart Chat is the secure conversational chat interface of Smart AI that helps you interact with connected enterprise systems.
It converts plain-language requests into **approved, secure API calls** and returns live answers from those systems.

## What you can do in Smart Chat

- Ask questions that return live operational data (for example orders, inventory, shipments, devices).
- Run approved actions and workflows (only when allowed by your role).
- Ask follow-up questions without repeating context.
- Turn results into summaries, charts, and dashboards.
- See what happened behind the scenes (when enabled for your role).

## Common use cases

- **Where is my order?** Get a single, trusted status even when data is split across systems.
- **Inventory check**: See stock levels for a SKU/location and get a consolidated view when configured.
- **Operational lookups**: Quickly pull details for orders, waves, locations, devices, shipments, and exceptions.
- **Cross-system workflows**: Ask once and let Smart AI coordinate multiple approved steps.

## Example prompts (warehouse)

- "Show me details of order 123."
- "Show me area information for Building 3PSTG."
- "Give me a list of all devices."
- "How many units of Product X are in Warehouse 5?"

## Why Smart Chat is different from “document chat”

Smart Chat is designed for operations and execution. Instead of only searching documents (PDFs, wikis, emails), it focuses on **structured, actionable integrations** (approved APIs/commands/workflows). That means you can get live, up-to-date results—and perform approved actions—without needing to know the underlying system details.

## Follow-up questions (context-aware)

After Smart AI returns a table or dataset, you can refine it:

- "Only show the delayed ones."
- "Group by status."
- "Show totals by warehouse."
- "Export this."

## Charts on a previous response

If the last response returned a dataset, you can request a visualization:

- “Create a pie chart from this.”
- “Show a bar chart by order type.”
- “Make a time-series chart by ship date.”

Supported chart types typically include **pie, line, bar, stacked, and bubble** (availability may depend on your deployment).

## Auto-generated dashboard

You can ask Smart AI to turn the latest dataset into an interactive dashboard.
Smart AI identifies key fields and data types and generates charts/metrics to highlight trends.

## What happens behind the scenes (simplified)

When you ask something in Smart Chat, Smart AI typically:

1. Understands your request (what you want + key details like order number, warehouse, SKU).
2. Matches it to an **approved Smart Function** (a pre-defined capability your organization allows).
3. Validates it (required inputs, allowed values, and permission checks).
4. Sends the request to the right system(s) and gathers results.
5. Returns the answer in a user-friendly format (table, summary, chart, dashboard).

For questions that span multiple systems, Smart AI can query systems in parallel and merge results into a single answer (so you don’t have to check multiple screens).

## “What did you do?” (transparency)

When enabled, Smart AI can show what it executed behind the scenes (for example, the MOCA command or API call).
This is useful for:

- validating the result
- troubleshooting unexpected answers
- learning how a request maps to an approved function

If you do not see this feature, your role may not have access to execution details.

## Security (what end users should know)

- Smart AI runs **approved functions only**. If something is not approved, it won’t run.
- Access is controlled by your role (you only see and run what you’re allowed to).
- For analytics (charts/dashboards), Smart AI can use a controlled approach: it may use column names (and sometimes a small sample) to understand how to summarize the data, while keeping full datasets protected inside your environment (depending on your organization’s settings).
