# Smart FX

Smart FX is the administrative experience for managing what Smart AI can do.
It is the “front face” where you configure, govern, and publish **approved functions** for your Smart AI instance.

If you are an end user who only chats with Smart AI, you may not need Smart FX.

## What Smart FX manages

- **Function catalog**: which functions exist for your instance/application.
- **Parameters & validation**: required inputs, allowed values, and safe defaults.
- **Permissions (RBAC)**: which roles can see or run which functions.
- **Versioning**: track changes over time and roll forward/back when needed.
- **Publishing**: make approved functions available to Smart Chat users.

## Smart Functions repository (Git)

Smart FX works with a Git-backed **Smart Functions** repository where the actual implementations live, such as:

- Blue Yonder MOCA commands
- REST call definitions
- scripts and cross-system workflows

When you publish changes in Smart FX, those changes are pushed to (or synchronized with) the Smart Functions repository
so they can be reviewed, versioned, and deployed consistently.

## Typical workflow

1. Create or update a function (name, description, parameters).
2. Validate and test the function in a controlled way.
3. Assign roles/permissions.
4. Publish to your Smart AI environment so Smart Chat can use it.

## Why Smart FX matters

Smart AI is powerful because it can call real enterprise systems.
Smart FX ensures that only the right functions are available to the right users, with the right guardrails.
