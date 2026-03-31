# Getting Started

## What you need

Smart Assistant sits on top of existing enterprise systems that already expose APIs 
(REST, proprietary protocols such as Blue Yonder MOCA, and others) — 
no replacement or migration of existing systems required.

Typical prerequisites:

- Access to the **target system endpoints** (e.g., WMS, ERP, CRM APIs).
- A **Git repository** to store approved functions (MOCA commands, REST definitions, 
  scripts, and cross-system workflows).
- A defined **security policy** (roles and permissions) controlling who can run 
  which functions.

## How users interact

Users submit natural language requests through one of the supported channels:

- **Microsoft Teams bot** — native chat interface within the Teams environment.
- **Web agent** (`smart-is.ai`) — browser-based access, no installation required.
- **Desktop app** — fully self-contained, suited for firewalled environments.

The Intelligence Engine extracts **intent + parameters** from the request, then 
executes only **pre-approved functions** through the hook layer — 
no ad-hoc or unauthorized system calls are possible.

## A simple example

**User:** *"How many units of Product X are in Warehouse 5?"*

1. The LLM identifies the approved function (`get_inventory`) and extracts 
   parameters (`product = Product X`, `location = Warehouse 5`).
2. The backend executes the internal system call (e.g., Blue Yonder MOCA) 
   entirely inside the **enterprise network**.
3. The user receives a structured response (e.g., `{ "inventory": 250 }`). 
   No business data is shared externally at any point.