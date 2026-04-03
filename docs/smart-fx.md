# Smart FX (SmartFX Studio)

Smart FX is where your team **builds and maintains the Smart Functions** that power Smart AI.
In simple terms: Smart FX is the “workbench” used to define what Smart AI is allowed to do, keep those capabilities consistent, and move changes through review.

If you only use **Smart Chat** to ask questions and run approved actions, you usually don’t need Smart FX.

## What is a Smart Function?

A Smart Function is an approved capability that Smart AI can use during a chat, such as:

- Looking up operational data (orders, inventory, shipments, devices, etc.)
- Running an approved action or workflow (when allowed)
- Calling an enterprise integration (API, command, or script) behind the scenes

Smart FX helps you keep these functions clear for end users and safe for production systems.

## What you can do in Smart FX

### Organize work with projects and systems

- Create/open projects connected to a Smart Functions Git repository
- Pick a “system” (a top-level folder) and browse the functions inside it

### Edit a function (details + implementation)

- Write or improve descriptions so users know what the function does
- Define inputs (what Smart AI needs to ask for) and outputs (what the function returns)
- Update the underlying implementation when needed (the app typically supports common script types used in your environment)

### Reuse shared building blocks

Smart FX commonly supports shared definitions so you don’t have to repeat yourself across many functions, such as:

- Tags (grouping and discovery)
- Domain fields (reusable “field” definitions like type, required/optional, and allowed values)
- Reusable input/output collections (common sets of fields used in many functions)

### Review changes with a Git-friendly workflow

- See what changed, view diffs, and revert files when something doesn’t look right
- Create a branch, commit, push, and open a pull request (depending on your deployment)

> Note: Making changes available in Smart Chat typically follows your normal release process (for example: PR review → merge → deployment). Smart FX helps you produce reviewable changes; it doesn’t replace your release controls.

### Use connections and testing tools (if enabled)

Depending on your environment, Smart FX may also include:

- **Connections & credentials** to external systems (managed through an integrations backend)
- **MCP servers** (generate/store MCP links and browse available tool lists)
- **Playground** to experiment with tool calling in a chat-like UI (often shows tool calls and steps)
- **Eval** to test tool selection reliability and export a report (for review/sharing)
- **Secure Chat**  Smart chat experience to interact with your enterprise systems via natural language.
- **Help panel** for searchable in-app documentation

## Common use cases

- **Developers/builders**: update a function and open a PR for review
- **Platform owners**: keep shared tags/domains/collections consistent across teams
- **QA/test teams**: run Eval to validate tool selection after changes
- **Integrations engineers**: manage connections and generate MCP server links
- **Product/demo teams**: use Playground to show “what the AI is doing” (tools used, steps, plan)

## Typical workflow

1. Open a project (connect Smart FX to your Smart Functions repository).
2. Select a system and choose a function to update.
3. Update the function details (description, inputs/outputs) and implementation if needed.
4. Review changes and test in Playground/Eval (if available).
5. Commit, push, and open a pull request for review.
