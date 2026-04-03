# Smart Chat

Smart Chat is where end users interact with Smart AI using natural language (Teams, web, or desktop).
It is built for **live operational data and workflows**—not just static document answers.

mart Chat is built inside **Smart FX** as **Secure Chat**. If you see a “Secure Chat” page, it’s the same Smart Chat experience—just accessed from within Smart FX.

## What you can do in Smart Chat

- Ask questions that return real-time data from connected systems (WMS/ERP/CRM).
- Trigger approved actions (only if your role allows it).
- Ask follow-up questions that build on the previous response.
- Generate charts and dashboards from the most recent dataset.
- Request transparency (for example: show the MOCA command / API call) when enabled for your role.

## Example prompts (warehouse)

- “Show me details of order 123.”
- “Show me area information for Building 3PSTG.”
- “Give me a list of all devices.”
- “How many units of Product X are in Warehouse 5?”

## Follow-up questions (context-aware)

After Smart AI returns a table or dataset, you can refine it:

- “Only show the delayed ones.”
- “Group by status.”
- “Show totals by warehouse.”
- “Export this.”

## Charts on a previous response

If the last response returned a dataset, you can request a visualization:

- “Create a pie chart from this.”
- “Show a bar chart by order type.”
- “Make a time-series chart by ship date.”

Supported chart types typically include **pie, line, bar, stacked, and bubble** (availability may depend on your deployment).

## Auto-generated dashboard

You can ask Smart AI to turn the latest dataset into an interactive dashboard.
Smart AI identifies key fields and data types and generates charts/metrics to highlight trends.

## “What did you do?”

When enabled, Smart AI can show what it executed behind the scenes (for example, the MOCA command or API call).
This is useful for:

- validating the result
- troubleshooting unexpected answers
- learning how a request maps to an approved function

If you do not see this feature, your role may not have access to execution details.
