# Architecture

## Core building blocks

### User channels

Users can interact with the system through three channels:

- **Microsoft Teams bot** — native chat interface for quick access within the Teams environment.
- **Web agent** (smart-is.ai) — browser-based access from anywhere, no installation required.
- **Desktop app** — fully self-contained, suited for firewalled environments where all data must stay on-premise.
### Smart-IS Intelligence Engine

The Intelligence Engine is the orchestration layer that:

- Converts user input into a resolved function call, extracting the correct intent and parameters.
- Manages session context to support coherent, multi-turn follow-up conversations.
- Logs and monitors every interaction for auditing, performance tracking, and troubleshooting.
### Component Hook Library

The **Component Hook Library** sits between the **Intelligence Engine** and the **target systems**, acting as a secure validation and invocation layer. It:

- **Validates** the resolved function name and parameters before any system call is made.
- **Enforces** authentication and authorization policies to ensure only permitted actions are executed.
- **Invokes** the approved implementation from the Git-managed repository for the requested function.

### Smart-Functions

The Smart-Functions repository stores reusable, pre-approved business logic that powers every system call, such as:

- **Blue Yonder MOCA commands** — proprietary warehouse management queries and operations.
- **REST endpoint definitions** — call templates for systems like SAP, Manhattan, and Salesforce.
- **Cross-system workflows** — orchestrated sequences that chain multiple APIs into a single business operation.

## End-to-end request flow

1. **User request:** User types a natural language query (e.g., "Show me detail of order 123").
2. **LLM interpretation:**  The LLM extracts a function name + parameters (e.g., get_order_details(order_id=123)).
3. **Orchestration:** The Intelligence Engine resolves intent-to-function and orchestrates the API call.
4. **Validation + lookup:** The hook layer validates the request and consults Smart Functions repository for the correct system call.
5. **System invocation:** The appropriate protocol (MOCA, REST, etc.) is executed against the target enterprise system.
6. **Response handling:** Results are validated, formatted, and returned to the user.
## Security model

- **Keep sensitive enterprise data inside the organization's network.**
All backend execution happens entirely within the enterprise network. Only the final result is delivered to the user's device.
- **Send only non-sensitive information** externally for intent extraction.
The LLM receives only the user's query text and function metadata. The actual business data behind it is never shared externally.
- **For analytical requests**, share only metadata; run full processing internally.
For visualizations or breakdowns, the **LLM receives only column names** by default — no row data is shared unless the user explicitly chooses to. The full dataset is processed and charted entirely inside the enterprise network.

## Deployments

### On-premise deployment

- The **Intelligence Engine** and hook layer run inside the internal network, protected by firewall.
- Sensitive data remains local; only minimal non-sensitive information is shared externally for intent recognition.

### Cloud deployment

- The Intelligence Engine is hosted on **Azure**, accessible from anywhere via **web** or **Microsoft Teams.**
- Only **non-sensitive inputs** are processed externally, while encryption and controlled API gateways protect sensitive data.

