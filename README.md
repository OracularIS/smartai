# Smart Assistant
Smart Assistant (Smart IS Conversational API Framework) is a low-code platform that turns natural language requests into **secure, validated API calls** against enterprise systems such as WMS, ERP, and CRM platforms.

Instead of building and maintaining many custom screens, static reports, and one-off integrations, Smart Assistant uses:

- A **Smart-Functions repository** (Git-managed scripts such as MOCA commands and REST call definitions).
- A **Component Hook Library** that validates requests (authN/authZ, parameter validation) and exposes functions as standardized APIs.
- A **Smart-IS Intelligence Engine** that uses an LLM to extract *intent + parameters* from user text, then orchestrates only approved function calls.

## Key capabilities (from the white paper)

- **Natural language access:** Users ask questions like “Show open orders for Warehouse B” without learning API syntax.
- **API-centric (actionable):** Focuses on structured enterprise APIs (not just document Q&A).
- **Low-code onboarding:** Configure integrations via JSON + Git-managed scripts/workflows.
- **Multi-channel:** Microsoft Teams bot, web agent, and desktop app options.
- **Security-first design:** Keep sensitive data inside the enterprise network; send only minimal intent/metadata to the external LLM.

## Next pages

- [Getting Started](./docs/getting-started.md)
- [Architecture](./docs/architecture.md)
- [Use Cases](./docs/use-cases.md)
- [FAQ](./docs/faq.md)

