# Overview

## What is Smart AI?

Smart AI (Smart IS Conversational API Framework) helps teams get answers and complete routine work across enterprise systems using plain language.
You ask a question (or request an approved action) in chat, and Smart AI turns that request into **secure, validated calls**
to systems like WMS, ERP, and CRM—without needing to learn system-specific screens or API details.

Smart AI is designed for **live, actionable operations** (real-time data and workflows), not just document Q&A.

## Smart AI components

Smart AI is organized into three major components:

- **Smart Chat**: The end-user chat experience (Teams, web, or desktop) where you ask questions, follow up, and
  request summaries, tables, charts, or approved actions.
- **Enterprise Mesh**: The security and connectivity layer that checks permissions, validates inputs, and routes approved requests
  to the right enterprise system before anything runs.
- **Smart FX (SmartFX Studio)**: The builder/admin workspace where your team manages the **Smart Functions** that Smart AI can use.
  This is where you define what each function does, what inputs it needs, and what it returns—then move changes through review
  using a Git-based workflow (diffs, revert, commits, and pull requests). Some deployments also include Connections, MCP, Playground, and Eval.

Most end users spend their time in **Smart Chat**. Smart FX is typically used by builders, admins, QA, and integration teams.

> Depending on your deployment, Smart Chat may be available inside Smart FX as **Secure Chat** (a built-in chat page that provides the same Smart Chat experience).

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
