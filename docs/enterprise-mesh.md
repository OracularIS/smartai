# Enterprise Mesh

Enterprise Mesh is the secure connective tissue of Smart AI.
It connects Smart Chat requests to your approved enterprise system integrations—safely and consistently.

At a high level, Enterprise Mesh is “query-centric”: instead of moving and syncing data between systems, it can
send the query to the systems and combine the results into one trusted answer (based on what your organization has
approved and configured).

## What Enterprise Mesh does

- **Routes requests** to the right system (WMS/ERP/CRM) using the right protocol (REST, MOCA, etc.).
- **Validates inputs** (required parameters, formats, allowed values) before anything runs.
- **Enforces permissions (RBAC)** so users can only run what they are allowed to run.
- **Uses approved implementations** from the Smart Functions Git repository (scripts, MOCA commands, REST definitions, workflows).
- **Standardizes access** so different systems feel consistent to end users in Smart Chat.

## Why it matters to end users

Enterprise Mesh is what makes Smart AI “actionable”:

- results come from live systems (not outdated documents)
- requests are governed (approved functions only)
- behavior is consistent across channels (Teams, web, desktop)

## Ask once, see everything (common scenarios)

Enterprise Mesh is most helpful when the answer you need is split across systems.

### Where is my order?

Order status can be fragmented across ERP, WMS, and TMS. Enterprise Mesh can:

1. query relevant systems in parallel
2. merge the responses into a single standardized dataset
3. apply configured reducer logic (precedence rules) to return a single definitive status

### True inventory for a SKU

A complete inventory picture can include multiple categories (for example: on-hand, in-transit, on-order).
Enterprise Mesh can query those sources and calculate a single “available-to-promise” style number (if configured).

## How answers are produced (simplified)

Depending on the function, Enterprise Mesh may perform:

- **Federated queries**: parallel requests to multiple systems using native protocols (REST, MOCA, SQL, etc.).
- **Live aggregation**: merge responses into one unified dataset in real time.
- **On-the-fly transformation**: filter, group, or calculate fields on the merged dataset to produce the final answer.
- **Unified API + security**: expose a single secure endpoint to Smart AI, while keeping system-specific complexity hidden.

## Security and data handling (high level)

Smart AI is designed so that sensitive enterprise data remains inside your environment:

- the LLM is used primarily to interpret user intent and parameters
- execution happens through approved functions inside your controlled network boundary
- for analytics/visualizations, only limited metadata (and optionally a small sample) may be used to generate generic logic,
  while full processing runs internally

Your organization’s security policy determines exactly what is enabled and what can be shared.

## Tracking and auditability (what you may notice)

Your organization may enable tracking so administrators can troubleshoot safely without exposing business payloads.
Depending on configuration, this can include:

- who asked, when, and which approved function ran
- masked parameters and high-level schema details (for example: column names or row counts)
- run IDs and step timings for support and audits
