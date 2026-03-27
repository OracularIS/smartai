# FAQ

## Is Smart Assistant just document search (RAG)?

No. The white paper positions Smart Assistant as **API-centric**: it focuses on calling structured enterprise APIs to retrieve data and trigger workflows, rather than only answering questions from unstructured documents.

## Does sensitive data get sent to the external LLM?

The security model described in the white paper is designed to keep sensitive data inside the enterprise boundary. The LLM is used for intent extraction (and, for analytical requests, may receive limited metadata + small samples to generate generic logic).

## How does it translate a user question into an API call?

At a high level:

1. The LLM extracts intent + parameters.
2. The Intelligence Engine maps that intent to a pre-approved function.
3. The Component Hook Library validates and executes the function against the target system.

## How does it keep context for follow-up questions?

The white paper mentions context retention as a core requirement. The implementation typically uses session memory so follow-up questions can reference prior responses.

