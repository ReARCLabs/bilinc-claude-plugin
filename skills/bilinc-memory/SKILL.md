---
name: bilinc-memory
description: Use Bilinc Cloud memory to persist decisions, facts and context across sessions. Use when the user asks to remember something, recall earlier context, correct a stored fact, or checkpoint and restore memory state.
---

# Bilinc memory

Bilinc stores memory entries in the user's Bilinc Cloud workspace through the `bilinc` MCP server.

## Tools

- `commit_mem`: write an entry. Writing to an existing key revises it. Pass `idempotency_key` when retrying.
- `recall`: read entries by key or memory type before answering questions about earlier work.
- `revise`: deliberately change a stored value. Pass `expected_version` from an earlier read to avoid overwriting a newer value.
- `forget`: delete an entry. Only do this when the user asks, and give a `reason`.
- `snapshot`: checkpoint the current memory state before a risky change.
- `diff`: compare the current state with a snapshot.
- `rollback`: restore a snapshot. Confirm with the user first, because it replaces current state.
- `status`: check the connection and workspace state.

## Guidance

- Recall before you write, so a new entry doesn't duplicate or contradict an existing one.
- Use stable, descriptive keys, for example `project:<name>:decision:<topic>`.
- Store decisions and facts the user confirmed, not guesses.
- Never store secrets, credentials or API keys in memory.
