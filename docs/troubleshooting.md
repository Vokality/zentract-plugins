# Troubleshooting

Use this page if Zentract does not appear or does not connect after installation.

## Codex

If Codex cannot find the marketplace, confirm it was added:

```bash
codex plugin marketplace list
```

If the marketplace is missing, add it again:

```bash
codex plugin marketplace add Vokality/zentract-plugins --ref main
```

If the plugin is installed but Zentract tools do not appear, start a new Codex thread. Codex loads plugin tools when a new thread starts.

## Claude Code

If Claude Code cannot find the marketplace, add it again:

```text
/plugin marketplace add Vokality/zentract-plugins
```

If the plugin is installed but Zentract tools do not appear, reload plugins:

```text
/reload-plugins
```

If the marketplace was added earlier, refresh it:

```text
/plugin marketplace update zentract-plugins
```

## Cursor

Try the one-click install link first:

[Add Zentract to Cursor](https://cursor.com/en-US/install-mcp?name=Zentract&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vemVudHJhY3QuaW8vbWNwIn0%3D)

If the one-click install link does not open Cursor, add Zentract manually to `~/.cursor/mcp.json`:

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

After saving, restart Cursor or reload the window.

If Zentract still does not appear, open Cursor's MCP settings and confirm that `Zentract` is listed and enabled.

## Zentract Authorization

Public Zentract questions, such as product, pricing, FAQ, and API discovery, do not require account authorization.

Account-specific actions, such as listing tasks or starting timers, require Zentract authorization. If the client reports that authorization is missing or expired, reconnect Zentract from the client’s plugin authorization prompt.

## Connectivity Check

To verify that the public Zentract connection is reachable:

```bash
curl -sS -X POST https://zentract.io/mcp \
  -H 'Content-Type: application/json' \
  --data '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

The response should include public tools such as product overview, pricing, FAQ, and API discovery.
