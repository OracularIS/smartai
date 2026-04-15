# MCP (Model Context Protocol)

MCP (Model Context Protocol) is a standard way for AI clients (like Claude Desktop) to discover and call **tools**.

In Smart AI, an MCP server exposes a curated set of **approved Smart Functions** from a specific **project + system** so external clients can:

- List the tools you published (names, descriptions, input schema)
- Call those tools with validated parameters
- Receive structured results back (tables/JSON), just like Smart Chat

This page stays intentionally short on “what is MCP” and focuses on **what it does in Smart AI** and **how to use it end-to-end**.

---

## When you should use MCP with Smart AI

Use MCP when you want Smart AI’s governed enterprise tools to be available **outside** the Smart AI UI:

- **Run enterprise lookups from a desktop AI client** (e.g., check order status without switching apps)
- **Standardize access**: one governed tool catalog for multiple clients (desktop, IDE, agents)
- **Enable automation**: compose Smart Functions inside larger agent workflows

If your goal is only “chat with enterprise systems”, Smart Chat is usually the fastest path. MCP is best when you need **tool access in another client**.

---

## Prerequisites (what must exist before MCP will be useful)

Before generating an MCP server, make sure these are already done:

1. **Project is connected to a Smart Functions repository**
   - This is where your Smart Functions (code + metadata) live and are versioned.
2. **Functions are in a usable state**
   - Good descriptions, correct inputs/outputs, and tested in Dev Console.
   - (Recommended) An Eval run looks good for the functions you plan to expose.
3. **Connections + credentials are configured**
   - MCP tools call the same governed functions; they still need working connections.


---

## Create an MCP server in Smart FX

1. Go to **MCP Servers**
2. Click **Generate New MCP Server Link**
3. Select the **system** (for example: `Enterprise`)
4. Enter a clear server name
5. Click **Generate Link**

After generation, open the MCP server link to view details:

- **Server URL**
- **Connections** bound to this server/system
- The **tool list** (your Smart Functions) that clients will discover and call

---

## What the MCP Server Details page is telling you

### Tool list

This is the contract external clients will see. Tools appear here only if they are:

- In the selected project/system scope
- Approved/published (depending on your org’s governance settings)
- Valid enough to be exposed (metadata and schema are required)

### Connections

Tools can fail even when schemas look correct if the server is pointing to the wrong connection/environment.
Treat “connections shown here” as the **runtime wiring** for MCP calls.

### Export

The **Export** section is the safest source of truth for client setup. It typically provides:

- Client-specific configuration snippets
- Any required auth headers/tokens (if your org requires them)
- Notes on supported transport (HTTP/SSE/stdio) for that client

---

## Add the server to Claude Desktop (example)

Claude Desktop supports MCP servers via a local configuration file (Windows/macOS/Linux paths vary).

1. In Smart FX → your MCP server → **Export**, choose **Claude Desktop**
2. Copy the generated configuration snippet
3. Paste it into Claude Desktop’s config file
4. Restart Claude Desktop
5. Verify the tools appear and run a test call

### Example config shape (Claude Desktop)

Your exported snippet may differ (auth headers, naming, transport). This is the general pattern Claude uses:

```json
{
  "mcpServers": {
    "smartai-enterprise-dev": {
      "type": "http",
      "url": "https://YOUR_SMARTAI_MCP_SERVER_URL",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_IF_REQUIRED"
      }
    }
  }
}
```

If your export uses a different transport (for example `sse` or `stdio`), keep the exported values as-is.

Reference: Claude MCP configuration docs:
`https://docs.claude.com/claude-code/mcp`

---

## Test the MCP server end-to-end

Once Claude Desktop is restarted:

1. Ask Claude to **list available tools** (or open the tools panel)
2. Pick one tool (for example, an order lookup function)
3. Run it with a real parameter value
4. Confirm:
   - The tool call succeeds
   - Results match what you see in Smart FX Dev Console
   - The function’s output shape is usable (columns/fields are meaningful)

If a tool is hard to use from Claude, it usually means the **function metadata** needs work (descriptions, input schema, or output naming).

---

## Troubleshooting

- **No tools appear**
  - Confirm you selected the correct project/system when generating the server.
  - Confirm functions are approved/published and have valid metadata.
- **Tools appear but fail**
  - Confirm the MCP server details show the correct connection/environment.
  - Confirm credentials exist for that connection.
- **Tool calls require extra parameters**
  - Improve metadata: add required inputs, enums, and clear descriptions.
  - Use Dev Console to test multiple parameter combinations before exposing via MCP.
- **Multiple clients / multiple environments**
  - Use separate MCP servers per environment (`dev`, `qa`, `prod`) and name them accordingly.

---

## Enterprise setups: one server, many tools (and many files)

In larger orgs, it’s common for one MCP server to represent a **single tool catalog** (for example: “Enterprise / Dev”) that aggregates tools implemented across many files in your Smart Functions repository.

For details on repository patterns (including “one manifest/meta file referencing many function files”), see:

- [Smart Functions repository structure](./smart-functions-repository.md)
