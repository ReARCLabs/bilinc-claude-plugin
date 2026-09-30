---
name: bilinc-memory
description: Use Bilinc memory to keep decisions, facts and context across sessions. Use when the user asks to remember something, recall earlier context, correct or remove a stored fact, or compare and restore memory with checkpoints.
---

# Bilinc memory

Bilinc stores memories in the user's Bilinc workspace through the `bilinc` remote MCP server (`https://mcp.bilinc.space/mcp`).

## Tools

- `recall`: search memories with a natural-language query. Each result has a `version`, its source and when it last changed.
- `remember`: store a new memory under a key that does not exist yet. It never overwrites.
- `revise`: change an existing memory. Pass `expected_version` from `recall` so a newer value is never overwritten.
- `forget`: remove a memory from active recall, with a `reason`.
- `create_snapshot` / `list_snapshots`: save and list checkpoints of the whole workspace.
- `diff`: show what changed since a checkpoint, with before and after values.
- `preview_rollback` / `rollback`: see exactly what restoring a checkpoint would change, then restore it with the preview's confirmation token.
- `status`: show the workspace, plan and whether this connection can write.

## Guidance

- Recall before you write, so a new memory doesn't duplicate or contradict an existing one.
- Use stable, descriptive keys, for example `project.<name>.decision.<topic>`.
- Store decisions and facts the user confirmed, not guesses. Revise, forget or roll back only when the user asks for it or agrees.
- Show the rollback preview to the user before restoring a checkpoint.
- Never store secrets, credentials or API keys in memory.
