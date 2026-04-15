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

## Step 0: Prepare your Smart Functions repository

Before you add a project in Smart FX, create a Git repository (Azure DevOps/GitHub/etc.) that will store your Smart Functions.

1. **Create a new Git repository** on your chosen platform (Azure DevOps, GitHub, etc.)
2. **Pick a system name** you will build for first (e.g., Enterprise, Snowflake, Bugzilla). The folder name you create in the repository **is** the system name — Smart FX uses it to discover and identify the system.
3. **Create an initial folder structure** in your repository (recommended for first-time setup):
   - Create a top-level folder named after your system
   - Inside it, create a `base` folder
   - You can have multiple systems in the same repository, each as their own top-level folder
   
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

## Step 1: Access the Portal

Go to: https://smartfunctions.smart-is.com/

![Smart FX Login Page](.attachments/01_smartfx_login_page.png)

Click **Get Started Free** or **Sign In**.

---

## Step 2: Sign In

Login using:

- Email and Password  
- Microsoft  
- Google  

![SSO Login Page](.attachments/02-sso_login_page.png)

---

## Step 3: Create Your Project/Repository

Add your commands repository to SmartFX.

**What “adding a project” does (and why):**

- Connects Smart FX to a **Git repository** that becomes the source of truth for your tools
- Enables **version control and review** (commit messages, PRs, rollback)
- Makes your functions reusable across **Smart Chat, Eval, and MCP**

After logging in, create a project by providing:

- Enter Project Name  
- Add Repository Link  
- Provide Personal Access Token (PAT)  

Click **Clone & Create Project**.

![Add Your Project](.attachments/03_add-your_project.png)

---

## Step 4: View Your Projects

After creating your project, you will be taken to the Projects section.

Here, you will see a list of all your projects.

- Locate your project in the list  
- Double-click on the project to open it  

![View Your Project](.attachments/view_projects.png)

---

## Step 5: Work Inside Your Project

Once you open a project, the **Project Workspace** appears. This workspace includes:

- Code Editor (Smart Functions)  
- Meta (function description + inputs/outputs)  
- Tags  
- Input & Output Collections  
- Domains  
- Connections + credentials (system wiring)  
- Eval  
- Dev Console / Try It (test runs)  
- MCP Servers (optional export to external clients)  

![Project Page](.attachments/projects_page.png)

---

## Step 6: Quick Start Flow (Connection → Function → Test)

This is the shortest path to a working tool you can run in Dev Console and Secure Chat.

### 6.1 Create (or reuse) a connection

If you already have a connection for the system/environment you want (Dev/QA/Prod), skip to **Step 6.3**.

1. Open **Connections** → **New Connection**
2. Select the platform/system (options depend on your org setup)
3. Enter basics (Connection name, Environment)
4. Configure settings (Endpoints/URLs, auth method, any system-specific fields)

![Connection Page](.attachments/connections_page.png)

### 6.2 Add credentials to your connection

Credentials are stored in the platform so they are **not committed to Git**.

1. Open **Credentials** → **Add Credentials**
2. Select your connection from the dropdown
3. Add/update your credential details

![Add Credentials](.attachments/add_manage_credentials_page.png)

### 6.3 Create (or edit) a function and bind it to your connection

1. In the **Code Editor**, create a new function or open an existing one
2. In the top-right **Implementation** dropdown, select your system connection (this binds the function to that connection)
3. Keep Meta minimal but complete (description + tags + inputs/outputs)
4. Save → commit message → push to your repository (and PR if your workflow requires it)

### 6.4 Test in Dev Console / Try It

Run the function with real parameters against your connected environment (try a few parameter sets to validate edge cases).

### 6.5 Validate tool-calling with Eval

Use **Eval** to check that your function definitions are tool-calling ready (select system → create evaluation → select functions → review results).

---

## Step 7: Workspace Tour (Videos)

Use these if you want a UI walkthrough of each area.

### 7.1 Code Editor (Smart Functions)

<video controls width="1725">
  <source src=".attachments/projects.mp4" type="video/mp4">
</video>

### 7.2 Tags

Watch the video:

<video controls width="1725">
  <source src=".attachments/tags.mp4" type="video/mp4">
</video>

**What tags are for (and why they matter):**

- Help builders find and organize tools in Smart FX
- Help Smart AI route and select tools more reliably (especially when tools overlap)
- Provide a consistent vocabulary across teams (“orders”, “inventory”, “shipping”)

In the Tags section, you can:

- Create categories, subcategories, and topics  
- Edit or delete tags  
- Activate or deactivate them  

**Creating new tags can change behavior.** New or inconsistent tags can make tool selection worse (duplicates, near-synonyms) and can affect governance workflows in some orgs. Prefer existing tags when possible.

---

### 7.3 Input & Output Collections

Watch the video:

<video controls width="1725">
  <source src=".attachments/input_output.mp4" type="video/mp4">
</video>

Here you can:

- Create new collections  
- Edit existing ones  
- Delete collections  

Use collections to reuse consistent argument/response groups across many functions (for example, a shared `order_id` input definition or a common “order header” output shape).

---

### 7.4 Domains

Watch the video:

<video controls width="1725">
  <source src=".attachments/domain.mp4" type="video/mp4">
</video>

In the Domains section, you can:

- View all existing domains  
- Add new domains  
- Delete domains  
- Import domains using a .json file  

Domains help you standardize field definitions across tools (type, required/optional, allowed values, descriptions). This improves consistency and makes downstream charts/dashboards more reliable.

---

### 7.5 Eval

Watch the video:

<video controls width="1725">
  <source src=".attachments/eval.mp4" type="video/mp4">
</video>

The **Eval** section allows you to validate your Smart Functions against AI models to ensure they are configured correctly.  

Steps:

1. **Select a System**  
   - Choose the system you want to evaluate functions for (e.g., Enterprise).

2. **Create Evaluation**  
   - Click **Create Evaluation** to start the process.  
   - All available functions for the selected system will appear.

3. **Select Functions**  
   - Choose one or more functions to evaluate.

4. **AI Model Evaluation**  
   - The system evaluates function definitions against AI models.  
   - It checks for issues such as tool-calling errors or configuration problems.

5. **View Results**  
   - Evaluation results are displayed in the interface.  
   - You can download the results or export them to your repository as a PDF.

This ensures that all your functions are properly configured and ready for use with Smart AI.

---

## Step 8: Configure MCP Server for Your Functions (optional)

MCP (Model Context Protocol) allows your business functions to be used across external systems like Claude, OpenAI, and Copilot.
 
### Demo Walkthrough  
<video controls width="1725">
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

---

## Multi-Client Configuration  

Users can also:

- Select different **clients**  
- Access their respective configurations  
- Follow client-specific setup steps directly from the **Export** section  

For a full MCP page (including Claude Desktop setup + testing), see:

- [MCP (Model Context Protocol)](./mcp.md)

---
## Step 9: Secure Chat

Smart Chat is the secure conversational chat interface of Smart AI that helps you interact with connected enterprise systems securely without exposing the actual data values to LLM.

- Smart Chat allows you to execute your function operations via natural language, schedule workflows, and perform analysis on your data.

- It employs a code generation strategy for analysis and operations that runs in an isolated environment. Only the meta data is shared with the LLM that helps it to generate code for insights such as bar charts, line charts, filtering data etc.

- Users can generate live charts via natural commands and see the actual command that the LLM invoked behind the scenes for observability. 

Watch the demo:

<video controls width="1725">
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

## Notes

- All actions are secure and controlled  
- Only approved functions can run  
- No direct system access is allowed  
- Keep your Smart App Keys secure  

---

## You're Ready

You can now start exploring and using Smart AI effectively.
