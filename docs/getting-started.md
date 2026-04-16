# Getting Started with Smart AI

Smart AI is an intelligent platform that allows you to connect to enterprise systems, add and manage your business logic, and interact with your data using simple, natural language. You can trigger business workflows, retrieve insights, and leverage AI-powered analysis through easy, conversational commands—making complex operations simple and accessible.

---

## Prerequisites

Before getting started, make sure you have:

1. A valid account (SSO / Email login)
2. A Git repository URL for your Smart Functions (your tool catalog)
3. A Personal Access Token (PAT) with repo access (if required by your Git provider)

---

## What you will accomplish in this guide

By the end, you will have:

- A Smart FX project connected to your Git repository
- A working connection + credentials for a target system/environment (Dev/QA/Prod)
- At least one function you can run in Dev Console (with validated inputs/outputs)
- An Eval run that checks tool-calling readiness
- A verified run in Secure Chat
- (Optional) An MCP server you can export and use in an external client

---

## What is a Smart Function?

A Smart Function is a named, documented capability that tells Smart AI what your enterprise system can do. Think of it as a card that says: "Here's what this action is called, what it needs as input, and what it returns."

Your functions live in a Git repository — that's what you'll set up next. Once connected, Smart AI can discover and call them through natural language in Secure Chat.

---

## Prepare your Smart Functions repository

Before adding a project in Smart FX, set up a Git repository to store your Smart Functions.

## Quick Setup

1. Create a new Git repository (Azure DevOps, GitHub, etc.)
2. Create a folder for your system (e.g., `Enterprise`, `Snowflake`, `Bugzilla`)  
   - This folder name becomes your system name in Smart FX
3. Inside it, add a `base` folder
   
   ```
    Enterprise/
    └── base/
    Snowflake/
    └── base/
    Bugzilla/
    └── base/
   ```

4. **Push your initial repository** to the remote Git platform

**Why this matters:** Many deployments expect functions to live under a consistent base folder so the platform can discover them reliably. If your organization uses a different structure/template, follow your internal standard.

---

## Access the Portal

Go to: https://smartfunctions.smart-is.com/

![Smart FX Login Page](.attachments/01_smartfx_login_page.png)

Click **Get Started Free** or **Sign In**.

---

## Sign In

Login using:

- Email and Password  
- Microsoft  
- Google  

![SSO Login Page](.attachments/02-sso_login_page.png)

---

## Create Your Project/Repository

A project connects Smart FX to your Git repository — this is where your functions live, get versioned, and become available across Smart Chat, Eval, and MCP. Once linked, any changes you push to the repo are automatically reflected in the platform.
 
After logging in, fill in your:
 
- Project Name  
- Repository Link  
- Personal Access Token (PAT)  
Then click **Clone & Create Project**.

![Add Your Project](.attachments/03_add-your_project.png)

---

## View Your Projects

After creating your project, you will be taken to the Projects section.

Here, you will see a list of all your projects.

- Locate your project in the list  
- Double-click on the project to open it  

![View Your Project](.attachments/view_projects.png)

---

## Work Inside Your Project

Once you open a project, the **Project Workspace** appears. Work through the sections below in order — each one builds on the last.

---

## Configure Your Project Workspace

### 1. Smart Function Editor
 
A Smart Function is an enterprise intent — a named, documented capability that tells the AI what your system can do and how to do it. Each function includes a plain-English description, defined inputs, and defined outputs.

Smart FX provides an integrated environment to define, document, and publish these intents, regardless of implementation. Under the hood, functions are built using Python, SQL, or MOCA.

All functions are stored in your Git repository, giving you version control, pull requests, rollback, and auditability out of the box.
 
**To create or edit a function:**
 
1. In the **Code Editor**, create a new function or open an existing one
2. In the top-right **Implementation** dropdown, select your system connection (this binds the function to that environment)
3. Fill in Meta: a clear description, tags, and input/output definitions
4. Add the code logic for what your function will do in the code section.
5. Save → add a commit message → push to your repository (create a PR if your workflow requires it)
6. Run the function in Dev Console with real parameters to confirm it works

![Project Page](.attachments/projects_page.png)
 
 --- 

> _Walk through creating a function in the Code Editor, binding it to a connection, filling in Meta, testing via Dev Console, and pushing it to your repository._
 
<video controls width="800">
  <source src=".attachments/projects.mp4" type="video/mp4">
</video>

---

### 2. Tags

Tags help Smart AI choose the right function when similar tools exist, preventing misrouting (like returning shipping data for an orders query). They also create a consistent shared vocabulary as your catalog grows.

In the Tags section, you can:

- Create categories, subcategories, and topics  
- Edit or delete tags  
- Activate or deactivate them  

Every function, domain, and collection supports this tagging framework, making it straightforward to manage and discover objects across your entire catalog as it grows.


> _See below how to create tag categories and assign them to functions to improve tool discovery and AI routing accuracy._

<video controls width="800">
  <source src=".attachments/tags.mp4" type="video/mp4">
</video>


### 3. Input & Output Collections

Collections let you define reusable input and output schemas once and share them across functions, improving consistency and eliminating duplication. Updates happen in one place, making changes easier to manage.

> _Learn how to define a reusable input or output schema once and reference it across multiple functions._

<video controls width="800">
  <source src=".attachments/input_output.mp4" type="video/mp4">
</video>

Here you can:

- Create new collections  
- Edit existing ones  
- Delete collections  

Use collections to reuse consistent argument/response groups across many functions (for example, a shared `order_id` input definition or a common “order header” output shape).

### 4. Domains

Domains are your *enterprise shared vocabulary* — the same way humans think about orders, waves, inventory, and statuses. They define standard field types, validation rules, allowed values, and descriptions used across your system, ensuring fields like customer_id behave consistently in every function, report, and dashboard.

Domains also support enums — predefined lists of allowed values — allowing users to query and filter using natural terms instead of system codes.

> _Set up shared field definitions — including enums — so that field types and allowed values stay consistent across all your functions._

<video controls width="800">
  <source src=".attachments/domain.mp4" type="video/mp4">
</video>

In the Domains section, you can:

- View all existing domains  
- Add new domains  
- Delete domains  
- Import domains using a .json file  

Domains help you standardize field definitions across tools (type, required/optional, allowed values, descriptions). This improves consistency and makes downstream charts/dashboards more reliable.

### 5. Evaluate your Function
 
Eval validates that your functions will be correctly identified and called by AI models. It simulates real-world tool selection under load, detects overlapping descriptions, missing arguments and ambiguous definitions before users encounter them. This is the final quality check before deploying functions to production chat.

> _Watch a full evaluation run: selecting functions, reviewing AI-generated test questions, and reading the scored results report._

<video controls width="800">
  <source src=".attachments/eval.mp4" type="video/mp4">
</video>

Steps:

1. **Select a System**  
   - Choose the system you want to evaluate functions for (e.g., Enterprise).

2. **Create Evaluation**  
   - Click **Create Evaluation** to start the process.  
   - Changed or newly created functions are highlighted at the top with badges.

3. **Select Functions**  
   - Choose one or more functions to evaluate. The system will automatically load *all* functions in your system during testing to detect real-world overlap.

4. **AI Testing**  
   The LLM automatically generates 10 natural language test questions per function, then attempts to call each function using standard OpenAI tool calling with your full tool catalog loaded.

5. **Scored Results**  
   You will receive a detailed report scored on:
   - 50% Correct function selection
   - 30% Required argument extraction
   - 20% Relevant optional arguments

   Results include full request/response traces. Reports are automatically saved to your repository in both JSON and PDF format for team review.

Evaluation runs fully on the server — you can safely navigate away and return later.

---

## Connections Setup

Connections define how Smart AI communicates with your external systems (e.g., Enterprise, BlueYonder).

A system represents the platform itself, while a connection represents a specific environment or instance of that system (such as Dev, QA, or Production).

Each system can have one or more connections, allowing you to work across multiple environments securely.

Connections act as the bridge between your functions and real systems, handling both:

- Where to send requests (endpoint/environment)
- How to authenticate (credentials)

Each function must be linked to a connection so it knows which system and environment to execute against.

If a connection for your system/environment already exists, you can reuse it. Otherwise:

1.  Go to Connections → New Connection

    You will see the main Connections overview page.

    ![Connections Overview Page](.attachments/connections_page.png)

2.  Select the target system/platform from the available list

    ![Select System Connection Type](.attachments/connection_select.png)

3.  Provide basic details:
    - Connection Name (e.g., `enterprise-dev`)
    - Environment (Dev / QA / Prod)

    ![Enter Connection Basic Details](.attachments/connection_details.png)

4.  Configure system-specific settings:
    - Base URL / Endpoint
    - Authentication type (API Key, OAuth, etc.)
    - Any required headers or config fields

    ![Configure Connection Settings](.attachments/configure_connection.png)

5.  Save the connection

---

## Add credentials to your connection

Connections define where to connect. Credentials define how to securely access it.

Credentials are stored securely in the platform and never committed to your Git repository.

1.  Go to Credentials → Add Credentials

    You will see the credentials management overview page.

    ![Credentials Management Page](.attachments/add_manage_credentials_page.png)

2.  Select your existing connection from the dropdown list
    - Enter authentication details:
      - API Keys / Tokens
      - Username / Password
      - OAuth configuration (if applicable)

    ![Select Connection and Add Credentials](.attachments/select_connection_and_update_add_credentials.png)

3.  Save credentials

---

## Configure MCP Server for Your Functions (optional)

MCP (Model Context Protocol) allows your business functions to be used across external systems like Claude, OpenAI, and Copilot.
 
### Demo Walkthrough  

> _See how to generate an MCP Server URL and integrate your functions with external clients like Claude or Copilot._

<video controls width="800">
  <source src=".attachments/mcp_server.mp4" type="video/mp4">
</video>

---

## Configuration steps  

### 1. Access MCP Servers  
Navigate to the **MCP Servers** section within the application.

### 2. Generate a New Server Link  
Click on **Generate New MCP Server Link** to begin setup.

### 3. Select Target System  
Choose the desired system (e.g., **Enterprise**) for which the MCP server will be configured.

### 4. Provide Server Details  
Enter a meaningful and identifiable **Server Name**.

### 5. Generate the Link  
Click **Generate Link** to create your MCP server endpoint.

### 6. View Generated Link  
The system will display a **server link** on the right-hand panel.

### 7. Open Server Details  
Click the generated link to navigate to the **MCP Server Details** page.

### 8. Review & Utilize Server Information  
On the MCP Server page, you can:

- Copy the **MCP Server URL**  
- View all configured **connections**  
- Explore available **MCP tools**, including:
  - Get Work Items  
  - Get User Information  
  - Additional system-specific tools  

### 9. Integration  
Use the copied **MCP Server URL** to integrate with your functions or external systems.

- The export option gives you guide on how to set up your MCP server on that platform such as Copilot, claude, OpenAI etc.

---
## Secure Chat

Smart Chat is the secure conversational interface of Smart AI, letting you interact with enterprise systems without exposing actual data to the LLM.

- Execute functions, schedule workflows, and analyze data using natural language
- Uses code generation in an isolated environment, sharing only metadata for insights (charts, filtering, etc.)
- Generate and customize live charts, and view the commands invoked for full observability


> _A live demo of querying a connected enterprise system in natural language and receiving instant results and visualisations._

<video controls width="800">
  <source src=".attachments/getting_started.mp4" type="video/mp4">
</video>

### Example

1. Open Secure Test  
2. Connect to a system  
3. Enter queries such as:

- Show me user information across the enterprise  
- Create a pie chart of users across systems  

You will receive:

- Instant results  
- Visualizations  
- Insights  

This is the primary way to interact with your system using natural language outside the project configuration.

---
