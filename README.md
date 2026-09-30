# Bilinc plugin for Claude

Connects Claude to [Bilinc](https://bilinc.space), verifiable long-term memory for AI agents. Claude can recall earlier decisions, remember new facts, revise or forget memories, and checkpoint, compare and restore memory across sessions.

## Requirements

- A Bilinc account at https://bilinc.space (free plan available, no card required)

Nothing is installed or run on your machine: the plugin points Claude at Bilinc's remote MCP server.

## What it adds

- The `bilinc` MCP server: `https://mcp.bilinc.space/mcp` (Streamable HTTP, OAuth 2.1)
- The `bilinc-memory` skill, which tells Claude when and how to use the memory tools

## Tools

| Tool | What it does |
| --- | --- |
| `recall` | Search memories; results carry a version, source and last-change time |
| `remember` | Store a new memory; never overwrites an existing key |
| `revise` | Change an existing memory, with an optional version check |
| `forget` | Remove a memory from active recall, with a reason |
| `create_snapshot` | Save a checkpoint of the workspace |
| `list_snapshots` | List checkpoints |
| `diff` | Show what changed since a checkpoint, with before and after values |
| `preview_rollback` | Show what restoring a checkpoint would change, without changing anything |
| `rollback` | Restore a checkpoint using the preview's confirmation token |
| `status` | Show the workspace, plan and whether the connection can write |

## Setup

1. Install the plugin.
2. Run `/mcp`, choose `bilinc` and select **Authenticate**.
3. Sign in on bilinc.space and approve the connection. You choose **Read only** or **Read & write**; a read-only connection never sees the write tools.

You can disconnect at any time from **Connected apps** in the Bilinc dashboard.

## Data and privacy

- **What it runs:** nothing locally. Claude connects to `https://mcp.bilinc.space/mcp` over HTTPS with an OAuth token that only works for that server.
- **What it sends:** when Claude calls a Bilinc tool, the tool's arguments (memory keys, values, queries, checkpoint parameters) go to Bilinc. Nothing else from your machine is sent.
- **Where data is stored:** in your Bilinc workspace, isolated from every other workspace. Every change is versioned, and `forget` removes a memory from recall. Retention and deletion are described in the privacy policy.
- Privacy policy: https://bilinc.space/privacy
- Terms: https://bilinc.space/terms

## Support

Issues: https://github.com/atakanelik34/Bilinc/issues

## License

This plugin repository is MIT licensed.
