# Bilinc plugin for Claude

Connects Claude to [Bilinc Cloud](https://bilinc.space), hosted memory for agents. Claude can write, recall, revise and forget memory entries, and checkpoint, compare and restore memory state across sessions.

## Requirements

- A Bilinc Cloud account and API key (`bil_live_...`), created in the dashboard at https://bilinc.space
- [uv](https://docs.astral.sh/uv/) installed (the plugin starts the MCP server with `uvx`)
- Python 3.10 or later

## What it adds

- The `bilinc` MCP server, which runs the `bilinc` PyPI package (`python -m bilinc.cloud_mcp`) and calls Bilinc Cloud with your API key
- The `bilinc-memory` skill, which tells Claude when and how to use the memory tools

## Tools

| Tool | What it does |
| --- | --- |
| `commit_mem` | Write a memory entry, or revise it if the key exists |
| `recall` | Read entries by key or memory type |
| `revise` | Change a stored value, with optional version check |
| `forget` | Delete an entry |
| `snapshot` | Checkpoint the current memory state |
| `diff` | Compare current state with a snapshot |
| `rollback` | Restore a snapshot |
| `status` | Check the connection and workspace state |

## Setup

Install the plugin, then enter your Bilinc API key when Claude prompts for it. The key is stored in your system's secure credential store.

## Support

Issues: https://github.com/atakanelik34/Bilinc/issues
