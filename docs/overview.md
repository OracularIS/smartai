# Overview

## What is Smart AI?

Smart AI is an enterprise AI solutions suite that enables teams to interact with and operate across enterprise systems using natural language.

Rather than being a standalone conversational API framework, Smart AI encompasses multiple components—including conversational interfaces (Smart Chat), intelligent execution engines, and secure integration layers.

It transforms user requests into **secure, validated, and actionable system operations** across platforms like WMS, ERP, and CRM—without requiring users to understand MOCA, REST APIs, or system-specific interfaces.

Smart AI is purpose-built for **real-time, operational workflows**, enabling live data access and execution—not just document-based Q&A.
## Smart AI components

Smart AI is organized into three major components:

- **Smart Chat**: The end-user chat experience (Teams, web, or desktop) where you ask questions, follow up, and
  request charts or summaries.
- **Enterprise Mesh**: The secure connectivity and governance layer that routes approved requests to the right
  enterprise system, enforces permissions, and validates parameters before anything runs.
- **Smart FX**: The admin-facing experience used to manage your Smart AI instance—configure and publish approved
  functions, permissions, and versions (backed by the Smart Functions Git repository).

## Key capabilities

- **Natural language → secure system calls**: Ask “Show open orders for Warehouse B” and get live results.
- **Follow-up questions (context-aware)**: Ask “Now show only the delayed ones” without restating everything.
- **Transparency when needed**: See what ran behind the scenes (e.g., the MOCA command / API call) when your role allows it.
- **Charts and dashboards**: Generate visuals from previously returned datasets with a follow-up prompt.
- **Security-first design**: Only approved functions can run; access is controlled via role-based permissions.

## Next pages

- [Getting Started](./getting-started.md)
- [Smart Chat](./smart-chat.md)
- [Smart FX](./smart-fx.md)
- [Enterprise Mesh](./enterprise-mesh.md)
- [FAQ](./faq.md)
