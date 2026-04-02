# Architecture

This page explains (at a high level) how Smart AI turns a user request into a secure interaction with enterprise systems.

## Core building blocks

### Smart Chat

Smart Chat is the secure conversational experience where you ask questions and request approved actions in natural language.
Smart AI is designed so that enterprise data is not exposed to an external LLM for API calling—only the minimum information
needed to interpret intent and parameters is used, while execution and business data remain inside your controlled environment.

### Smart AI Intelligence Engine

The Intelligence Engine is the orchestration layer that:

- interprets the user request (intent + parameters)
- maintains conversation context for follow-up questions
- coordinates execution and formats responses
- logs activity for auditing and troubleshooting (as configured)

### Enterprise Mesh (unifying siloed systems)

Enterprise Mesh is the secure validation and execution layer that:

- orchestrates requests across multiple enterprise systems (WMS/ERP/CRM) to solve the “siloed data” problem
- validates the requested function and parameters
- enforces authentication and role-based permissions (RBAC)
- calls the approved integration(s) using the right protocol (REST, MOCA, SQL, etc.)

### Smart Functions (Git repository)

The Smart Functions repository stores the approved implementations that power execution, such as:

- **Blue Yonder MOCA commands**
- **REST endpoint definitions** (SAP, Manhattan, Salesforce, etc.)
- **Cross-system workflows** (scripts that chain multiple steps into one operation)

Because Smart Functions are Git-managed, changes can be reviewed, versioned, and rolled out consistently.

### Smart FX

Smart FX is where we can configure and publish functions, parameters, and permissions for a Smart AI instance,
and synchronize those changes with the Smart Functions repository.

## End-to-end request flow

1. **User request:** A user asks a question in Smart Chat (for example: “Show me details of order 123.”).
2. **Intent extraction:** Smart AI interprets the request into an approved function name and parameters.
3. **Validation:** Enterprise Mesh validates the request (function exists, parameters are valid, user is authorized).
4. **Execution:** The approved implementation runs against the target system using the right protocol (MOCA, REST, etc.).
5. **Response:** Results are formatted and returned to the user (table, summary, chart, etc.).

## Security model (high level)

- **Approved functions only:** Smart AI can only run functions that have been published and approved.
- **Role-based access:** Users can only see and run what their role allows.
- **Data stays protected:** Execution runs inside your controlled environment; policies determine what is shared for intent recognition.
- **Analytics are controlled:** By default, **no cell/row data is shared with the LLM**—only column names and other metadata.
  If your organization enables it, users can choose to share more (for example, a small sample) to help generate generic processing logic,
  while full processing still runs internally.
