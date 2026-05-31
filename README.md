# Zentract Plugins

The official Zentract plugin marketplace and setup guide for Codex, Claude Code, and Cursor.

Install this marketplace to let supported clients answer Zentract product questions and, after authorization, work with your Zentract tasks, projects, clients, time entries, and timers.

## Install In Codex

Add the Zentract marketplace:

```sh
codex plugin marketplace add Vokality/zentract-plugins --ref main
```

Then open the Codex plugin browser and install `zentract@zentract-plugins`.

Start a new Codex thread after installation so Zentract tools are loaded.

## Install In Claude Code

From inside Claude Code, add the Zentract marketplace and install the plugin:

```text
/plugin marketplace add Vokality/zentract-plugins
/plugin install zentract@zentract-plugins
/reload-plugins
```

## Install In Cursor

Use the one-click install link:

[Add Zentract to Cursor](https://cursor.com/en-US/install-mcp?name=Zentract&config=eyJ0eXBlIjoiaHR0cCIsInVybCI6Imh0dHBzOi8vemVudHJhY3QuaW8vbWNwIn0%3D)

If your browser does not open Cursor from that link, add Zentract to your global Cursor MCP config at `~/.cursor/mcp.json`:

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

Restart Cursor or reload the window after saving the config.

## What The Plugin Adds

The `zentract` plugin adds:

- Product, pricing, FAQ, and API discovery answers for Zentract.
- Authorized access to Zentract tasks, projects, clients, time entries, manual time-entry creation, and timers.
- Timer actions when you explicitly ask to start or stop a timer.

Account-specific actions require Zentract authorization. If authorization is missing or expired, your client will prompt you to reconnect Zentract.

## Troubleshooting

See [docs/troubleshooting.md](docs/troubleshooting.md) if:

- The marketplace does not appear.
- The plugin installs but Zentract tools do not load.
- Zentract authorization is missing or expired.
- You want to verify the public Zentract connection is reachable.
