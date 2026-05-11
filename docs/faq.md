# FAQ

## What is SmartForge Nexes?

SmartForge Nexes is the **secure execution layer of SmartForge**.  
It connects SmartForge Cortex requests to approved enterprise systems, executes them in real time, and returns a **single, trusted answer**.

---

## How is SmartForge Nexes different from traditional integrations?

Traditional integrations rely on data replication (ETL) and point-to-point connections.

SmartForge Nexes is **query-centric**:
- No data copying or syncing  
- Queries run directly on source systems  
- Results are merged in real time  

This reduces latency, complexity, and maintenance.

---

## Does SmartForge Nexes store or replicate data?

No.  
SmartForge Nexes does **not store or duplicate data**. It executes queries directly on source systems and returns results in real time.

---

## How does SmartForge Nexes produce a single answer from multiple systems?

It combines several steps:

1. Runs **federated queries** across systems (ERP, WMS, TMS, etc.)  
2. Performs **live aggregation** of responses  
3. Applies **on-the-fly transformations** (filters, grouping, calculations)  
4. Uses **business-defined reducer logic** to select the final result  

The outcome is a single, consistent answer.

---

## What is SmartForge Cortex?

SmartForge Cortex is the **conversational interface of SmartForge** that lets users interact with enterprise systems using natural language.

You can:
- Retrieve live operational data  
- Run approved workflows  
- Ask follow-up questions  
- Generate charts and dashboards  

---

## How is SmartForge Cortex different from document-based chat (RAG)?

SmartForge Cortex is **API-centric**, not document-based.

| Feature | Document Chat | SmartForge Cortex |
|--------|--------------|-----------|
| Data source | Static documents | Live systems |
| Accuracy | Depends on documents | System-verified data |
| Actions | Not supported | Supported (approved only) |
| Freshness | Can be outdated | Real-time |

---

## Can SmartForge Cortex trigger actions or workflows?

Yes—but only if:
- The function is **pre-approved**
- The user has the required **permissions (RBAC)**

No arbitrary or unsafe actions can be executed.

---

## What is a function in SmartForge Studio?

A function is an **approved capability** that SmartForge can execute, such as:
- Fetching data (orders, inventory, shipments)  
- Running workflows  
- Calling APIs or system commands  

Each function includes:
- Implementation (code/script/API)
- Metadata (inputs, outputs, description)

---

## What is SmartForge Studio?

SmartForge Studio is the **builder studio** where teams create and manage functions.

It provides:
- function definition (metadata + implementation)  
- Connections to enterprise systems  
- Evaluation tools (to test AI tool selection)  
- Governance via Git  

---

## How does SmartForge turn a question into a system action?

1. User asks a question in SmartForge Cortex  
2. LLM extracts **intent + parameters**  
3. A matching **function** is selected  
4. SmartForge Nexes validates permissions and inputs  
5. The function executes on target systems  
6. Results are returned in a user-friendly format  

---

## Is sensitive data sent to the LLM?

No.

- The LLM only receives **user query + metadata**  
- **All execution happens inside your environment**  
- **No raw business data is exposed externally**  

For analytics:
- Only column names (and optional small samples) may be used  
- Full datasets remain internal  

---

## How is security enforced?

Security is built-in at multiple levels:

- **RBAC (role-based access control)**  
- **Approved functions only** (no arbitrary execution)  
- **Centralized validation and permissions**  
- **Secure API layer**  

Users can only access what they are authorized to see and run.

---

## Can users see what happened behind the scenes?

Yes (if enabled).

Users can:
- View executed commands or API calls  
- Understand how their request was processed  
- Troubleshoot results  

---

## Can SmartForge Cortex handle follow-up questions?

Yes.

SmartForge maintains **session context**, so users can:
- Refine results  
- Ask incremental questions  
- Build on previous responses  

---

## Can SmartForge Cortex generate charts and dashboards?

Yes.

From any dataset, users can:
- Create charts (pie, bar, line, stacked, etc.)  
- Generate dashboards automatically  
- Analyze trends without manual setup  

---

## What systems can SmartForge Nexes connect to?

Any system with an API, including:

- WMS (e.g., Blue Yonder, Manhattan)  
- ERP (e.g., SAP)  
- CRM (e.g., Salesforce)  
- Data platforms (e.g., Snowflake)  
- Custom REST / SQL / proprietary systems  

---

## How is activity tracked and audited?

SmartForge Nexes supports secure tracking, including:

- Who made the request  
- Which function was executed  
- Execution timing and run IDs  
- Masked parameters  

Sensitive data is **never logged or exposed**.

---

## When should we use SmartForge Nexes?

Use it when:
- Data is spread across multiple systems  
- Real-time answers are required  
- Actions must be secure and governed  
- A unified interface is needed  

---

## What makes SmartForge + SmartForge Nexes unique?

- No ETL or data duplication  
- Real-time, federated execution  
- API-driven (not document-based)  
- Built-in governance and security  
- Low-code extensibility via SmartForge Studio  

