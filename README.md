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

## Data and privacy

- **What it runs:** on startup, `uvx` downloads the pinned `bilinc==2.3.1` package from PyPI and runs `python -m bilinc.cloud_mcp` on your machine. The plugin has no hooks and runs nothing else.
- **What it sends:** when Claude calls a Bilinc tool, the MCP server sends that tool's arguments (memory keys, values, metadata, snapshot and diff parameters) to the Bilinc Cloud API at `https://bilinc.space` over HTTPS, authenticated with your API key. It sends no other files or data from your machine.
- **Where data is stored:** memory entries and snapshots are stored in your Bilinc Cloud workspace. You can delete entries with `forget`.
- Privacy policy: https://bilinc.space/privacy
- Terms: https://bilinc.space/terms

## Support

Issues: https://github.com/atakanelik34/Bilinc/issues

## License

This plugin repository is MIT licensed. The `bilinc` package it runs is licensed separately under BUSL-1.1; see https://github.com/atakanelik34/Bilinc.
