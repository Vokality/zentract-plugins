# Zentract Plugin

The Zentract plugin lets Codex and Claude Code work with Zentract.

## Components

- `skills/zentract/SKILL.md`: instructions for using Zentract account tools safely.
- `.mcp.json`: remote HTTP MCP server definition.
- `.codex-plugin/plugin.json`: Codex install-surface metadata.
- `.claude-plugin/plugin.json`: Claude Code plugin metadata.
- `assets/`: icon and logo used by Codex install surfaces.

## MCP Server

The bundled MCP server is:

```json
{
  "mcpServers": {
    "Zentract": {
      "type": "http",
      "url": "https://zentract.io/mcp"
    }
  }
}
```

Public tools can answer product, pricing, FAQ, and API discovery questions. Account tools require Zentract authorization.

## Smoke Test

Use this public JSON-RPC request to verify the MCP endpoint is reachable:

```bash
curl -sS -X POST https://zentract.io/mcp \
  -H 'Content-Type: application/json' \
  --data '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

The response should include public tools such as product overview, pricing, FAQ, and API discovery. Account tools may require authorization before use.

## Expected Client Behavior

After installation:

- Codex can load the bundled skill and MCP server in new threads.
- Claude Code can load the bundled skill and MCP server after `/reload-plugins`.
- Account-changing actions, such as starting or stopping timers, should only be called from explicit user intent.
