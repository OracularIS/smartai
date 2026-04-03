# FAQ

## Is Smart AI just document search (RAG)?

No. Smart AI is **API-centric**: it calls structured enterprise APIs to
retrieve live data and trigger real workflows, not just answer questions from
static documents. Unlike RAG, responses are always current and actionable.

## Does sensitive data get sent to the external LLM?

No. The LLM is used primarily for **intent extraction**. It receives the user's query
text and function metadata, not the underlying business data. For analytical requests,
only **column names** are shared by default to generate generic processing logic;
the full dataset is processed entirely inside the enterprise network. 
Sharing sample rows is **optional and controlled by the user**.

## How does it translate a user question into an API call?

1. The LLM extracts **intent + parameters** from the user's natural language query.
2. The **Intelligence Engine** maps that intent to a pre-approved function.
3. **Enterprise Mesh** validates and executes the function against the target system
   (for example: Blue Yonder MOCA, SAP REST, Salesforce).

## What enterprise systems does Smart AI connect to?

Smart AI connects to any system that exposes an API, including:
- **Blue Yonder WMS** (MOCA and REST)
- **SAP ERP** (REST)
- **Manhattan WMS** (REST)
- **Salesforce CRM** (SOAP/REST)
- **Snowflake** (SQL)
- Any other system with a REST or proprietary API endpoint.



## How long does it take to add a new integration?

With the low-code approach, a new integration typically takes **4–8 hours** 
(configure a JSON definition and upload the script to Git) compared to 
2–4 weeks of custom development in a traditional approach.

## What deployment options are available?

Two deployment models are supported:
- **On-premise:** The entire Intelligence Engine and hook layer run inside the 
  internal network. No sensitive data crosses the firewall.
- **Cloud (Azure):** The Intelligence Engine is hosted on Azure, accessible via 
  the web app, with controlled API gateways and encryption.

## Can users follow up on a previous query?

Yes. The Intelligence Engine maintains **session context** across a conversation, 
so follow-up questions are interpreted in light of previous exchanges without 
needing to repeat context.

## Can Smart AI generate charts and dashboards?

Yes. Users can request visualizations (pie, line, bar, stacked, bubble) from any
previously retrieved dataset with a plain-English follow-up. The system can also 
**auto-generate an interactive dashboard** from the most recent dataset 
automatically.

## How do we know what command ran behind the scenes?

Users can ask *"What did you do?"* at any time to see the exact MOCA command 
or API call that was generated and executed in response to their query.

## Who controls which functions users can access?

Access is governed by a **centralized RBAC (role-based access control)** policy.
Only pre-approved functions can be invoked, and users see only the data they are authorized to access.
Administrators manage functions and permissions through **Smart FX** (backed by the Smart Functions repository).
