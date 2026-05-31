# Zentract Plugins

Reusable Zentract plugins for agentic coding tools.

This repository hosts the Zentract plugin in marketplace formats for:

- Codex: `.agents/plugins/marketplace.json`
- Claude Code: `.claude-plugin/marketplace.json`

The plugin itself lives at `plugins/zentract/` and lets supported clients work with Zentract through the public Zentract MCP server at `https://zentract.io/mcp`.

## Repository Layout

```text
.
├── .agents/plugins/marketplace.json       # Codex marketplace catalog
├── .claude-plugin/marketplace.json        # Claude Code marketplace catalog
├── docs/
│   ├── development.md
│   └── zentract.md
└── plugins/
    └── zentract/
        ├── .codex-plugin/plugin.json      # Codex plugin manifest
        ├── .claude-plugin/plugin.json     # Claude Code plugin manifest
        ├── .mcp.json                      # Zentract MCP server config
        ├── assets/
        └── skills/zentract/SKILL.md
```

## Install In Codex

After this repository is pushed to GitHub, add the marketplace:

```bash
codex plugin marketplace add Vokality/zentract-plugins --ref main
```

Then open the Codex plugin browser and install `zentract@zentract-plugins`.

For testing from this local checkout before publishing:

```bash
codex plugin marketplace add /Users/lemi/code/zentract-plugins
codex plugin add zentract@zentract-plugins
```

Start a new Codex thread after installation so bundled skills and MCP tools are loaded.

## Install In Claude Code

After this repository is pushed to GitHub, add the marketplace from inside Claude Code:

```text
/plugin marketplace add Vokality/zentract-plugins
/plugin install zentract@zentract-plugins
/reload-plugins
```

For testing from this local checkout before publishing:

```text
/plugin marketplace add /Users/lemi/code/zentract-plugins
/plugin install zentract@zentract-plugins
/reload-plugins
```

## Zentract Plugin

The Zentract plugin bundles:

- A `zentract` skill with usage guidance.
- A Zentract connection configuration for `https://zentract.io/mcp`.
- Plugin metadata and visual assets for install surfaces.

See [docs/zentract.md](docs/zentract.md) for usage details and connectivity checks.

## Publishing Notes

- Keep the Codex and Claude marketplace files in sync when adding plugins.
- Keep plugin versions semver and bump versions when publishing changes.
- Public installation requires the GitHub repository to be public, or users must have access to the private repository through their git credentials.
- Official public directory submission is separate from hosting this marketplace repository.
