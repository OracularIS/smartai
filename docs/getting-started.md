# Getting Started

## What you need

Smart Assistant is designed to sit on top of existing enterprise systems that already expose APIs (REST, proprietary APIs such as Blue Yonder MOCA, and other protocols).

Typical prerequisites:

- Access to the target system endpoints (e.g., WMS/ERP/CRM APIs).
- A Git repository to store **approved functions** (scripts, MOCA commands, REST definitions, workflows).
- Defined security policy (roles/permissions) for who can run which functions.

## How users interact

Users submit natural language requests through one of the supported channels:

- **Microsoft Teams bot**
- **Web agent** (hosted at `smart-is.ai`)
- **Desktop app** (suited for fully firewalled environments)

The Intelligence Engine extracts intent + parameters, then executes only **pre-approved functions** through the hook layer.

## A simple example

User: “How many units of Product X are in Warehouse 5?”

1. LLM interprets an approved function (e.g., `get_inventory`) and parameters.
2. Backend runs the internal system call (e.g., Blue Yonder MOCA) inside the enterprise network.
3. User receives a structured response (e.g., `{ "inventory": 250 }`).
