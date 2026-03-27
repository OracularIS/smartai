# Use Cases

## Warehouse agent examples (from the white paper)

The white paper describes a “Smart Warehouse Agent” experience inside Microsoft Teams where users authenticate (e.g., with Blue Yonder credentials) and then ask warehouse questions in plain language.

Example prompts shown:

- “Show me detail of order 123”
- Request area information for a building (e.g., “Building 3PSTG”) and receive a structured table with fields such as short description, expected receipt area, and warehouse ID.
- “Give me list of all devices” and receive a structured table of device details (device codes, warehouse IDs, etc.).

## Follow-up questions

The white paper shows follow-up questions on a previous response (context-aware querying). Context retention is a core requirement for coherent multi-turn interactions.

## Analytics, charts & transparency

The white paper also describes:

- **Generate chart on previous response:** user requests pie/line/bar/stacked/bubble charts from the most recent dataset.
- **Auto-generated dashboard:** transforms the last retrieved dataset into an interactive visual summary by identifying key fields and data types.
- **“What did you do?” transparency:** users can view the exact MOCA command generated from an English query.
