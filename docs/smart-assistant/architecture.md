# Architecture

## Core building blocks (from the white paper)

### User channels

Users can interact with the system through:

- **Microsoft Teams bot**
- **Web agent** (hosted at `smart-is.ai` in the white paper)
- **Desktop app** (suited for fully firewalled environments)

### Smart-IS Intelligence Engine

The Intelligence Engine is the orchestration layer that:

- Converts user input into a resolved function call (intent + parameters)
- Manages session context for follow-up questions
- Logs and monitors activity

### Component Hook Library

The Component Hook Library sits between the Intelligence Engine and the target systems. It:

- Validates the resolved function name and parameters
- Enforces authentication/authorization policies
- Invokes the approved implementation for the function

### Smart-Functions repository (Git-managed)

The Smart-Functions repository stores reusable, pre-approved logic such as:

- Blue Yonder **MOCA commands**
- REST endpoint definitions / call templates
- Cross-system workflows (orchestration across multiple APIs)

## End-to-end request flow (from the white paper)

1. **User request:** user types a natural language query (e.g., “Show me detail of order 123”).
2. **LLM interpretation:** the LLM extracts a function name + parameters (e.g., `get_order_details(order_id=123)`).
3. **Orchestration:** the Intelligence Engine resolves intent-to-function and orchestrates the call.
4. **Validation + lookup:** the hook layer validates the request and consults the Git-managed function repository.
5. **System invocation:** the appropriate system call is executed (MOCA/REST/etc.) against the target enterprise system.
6. **Response handling:** results are validated/formatted and returned to the user.

## Security model (from the white paper)

- Keep **sensitive enterprise data** inside the organization’s network.
- Send only **non-sensitive information** externally for intent extraction.
- For analytical requests, share only **metadata** and a **small sample** to generate generic processing logic; run full processing internally.

## Deployments (from the white paper)

### On-premise deployment

- The Intelligence Engine and hook layer run inside the internal network.
- Sensitive data remains local; only minimal non-sensitive information is shared externally for intent recognition.

### Cloud deployment

- The Intelligence Engine is hosted in Azure.
- Users can access via web and Microsoft Teams, with controlled gateways and encryption.

