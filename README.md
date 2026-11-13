# agentdrive

Persistent file storage for AI agents. Your agent saves files over MCP, and each file gets a link a human can open.

- Site: https://useagentdrive.com
- MCP server: `https://useagentdrive.com/mcp` (Streamable HTTP, OAuth with PKCE S256)
- Free drive: 500 MB, 25 MB per file. Drive plan: $9/month, 50 GB, 1 GB per file.

## Tools

| Tool | What it does |
|---|---|
| `save_file` | Write text or binary files. Files above 2 MB upload in chunks. |
| `list_files` | List files, newest first. |
| `read_file` | Read a file back, whole or in chunks. |
| `get_file_link` | Get a browser link a human can open. |
| `delete_file` | Remove a file and revoke its link. |

Sign in at https://useagentdrive.com/signin first. Your free drive is created for you.

## Claude Code plugin

```
/plugin marketplace add plsoulie/agentdrive
/plugin install agentdrive@agentdrive
```

Then run `/mcp`, choose agentdrive and authenticate. The plugin adds the MCP server and one skill, `handoff`, which saves and loads a session handoff note.

Without the plugin, one command adds the server:

```
claude mcp add --transport http agentdrive https://useagentdrive.com/mcp
```

## Cursor

[Add to Cursor](https://cursor.com/install-mcp?name=agentdrive&config=eyJ1cmwiOiJodHRwczovL3VzZWFnZW50ZHJpdmUuY29tL21jcCJ9), or add this to `.cursor/mcp.json`:

```json
{ "mcpServers": { "agentdrive": { "url": "https://useagentdrive.com/mcp" } } }
```

## Codex

```
codex mcp add agentdrive --url https://useagentdrive.com/mcp
```

## Claude Desktop

Settings, Connectors, Add custom connector. Remote MCP server URL: `https://useagentdrive.com/mcp`

## Any MCP client

Streamable HTTP with OAuth discovery, public client registration and PKCE S256. Plain-text reference: https://useagentdrive.com/agent

## Links

- Guides, one per client and per job: https://useagentdrive.com/guides
- Plain-text setup guide for agents: https://useagentdrive.com/agent
- Site map for answer engines: https://useagentdrive.com/llms.txt
- Privacy: https://useagentdrive.com/privacy
- Official MCP Registry name: `com.useagentdrive/agentdrive` (see `server.json`)
- Contact: hello@useagentdrive.com

## License

The files in this repository are MIT licensed. The agentdrive service is hosted and is not open source.
