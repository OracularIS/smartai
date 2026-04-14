# Smart FX (SmartFX Studio)

Smart FX is the studio where your team **builds and maintains Smart Functions** (tools) that power Smart AI.
In simple terms: Smart FX is the workbench used to define what the AI is allowed to do, keep those capabilities consistent, and validate that tool calling stays reliable as things evolve.

## What is a Smart Function?

A Smart Function is an approved capability that Smart AI can use at runtime, such as:

- Looking up operational data (orders, inventory, shipments, devices, etc.)
- Running an approved action or workflow (when allowed)
- Calling an enterprise integration (API, command, or script) behind the scenes

In Smart FX, a function is treated as a combination of:

- **Implementation** (the code or script that runs)
- **Metadata** (the description, typed inputs, and expected output shape that the AI uses to choose and call it)

## Concept

Smart FX focuses on a few core areas:

- **Functions**: define and maintain tool behavior (metadata + implementation).
- **Metadata**: keep function definitions understandable and callable (arguments/response shape, descriptions).
- **Tags + domains**: standardize vocabulary (tags) and field schemas (domains) across many functions.
- **Connections**: bind functions to real external systems/environments without embedding credentials in code.
- **Eval**: measure whether the AI selects the right tools and arguments after changes.
- **Dev console**: troubleshoot builder and tool-calling behavior.

## Features (Smart FX scope)

### Functions (metadata + implementation)

- Browse projects/systems and find functions quickly.
- Edit a function’s metadata: description, inputs (arguments), and outputs (response shape).
- Edit the function implementation (script/API wrapper/etc.), depending on what your environment supports.

### Metadata building blocks (tags + domains)

- **Tags**: categorize functions for discovery and routing (what the tool is “about”).
- **Domain fields**: reusable field definitions (type, required/optional, enums, descriptions) used by many functions.
- **Reusable collections**: shared argument/response groups used to keep schemas consistent across tools.

### Connections

- View/manage connection records for external systems (per system/environment).
- Use connections to keep credentials/config out of function code while still enabling real integrations.

### Eval (tool selection validation)

- Run evaluations across selected functions/tools.
- Review results to confirm the AI chose the right tool and filled the right arguments.
- Export/share an evaluation report for review.

### Dev console (debugging)

- Inspect troubleshooting details for builder workflows and tool-calling flows (for example: request/session context and debug views).

## Common use cases

- **Developers/builders**: create or update Smart Functions (metadata + implementation).
- **Platform owners**: keep tags/domains/collections consistent across teams.
- **Integrations engineers**: manage connections used by functions.
- **QA/test teams**: run Eval to validate tool selection after changes.

## Typical workflow

1. Open a project (connect Smart FX to your Smart Functions repository).
2. Select a system and choose a function to create/update.
3. Update the function metadata (description, arguments, response) and implementation as needed.
4. Update tags/domains/collections if your change introduces new fields or categories.
5. Ensure the function is wired to the correct connection (if it calls external systems).
6. Run Eval to validate tool selection and argument filling before releasing the change.
