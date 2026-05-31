# Development

## Update The Existing Plugin

1. Edit files under `plugins/zentract/`.
2. Keep both manifests aligned:
   - `plugins/zentract/.codex-plugin/plugin.json`
   - `plugins/zentract/.claude-plugin/plugin.json`
3. Keep both marketplace catalogs aligned:
   - `.agents/plugins/marketplace.json`
   - `.claude-plugin/marketplace.json`
4. Bump the plugin version when publishing a change.
5. Validate JSON and plugin loading locally before pushing.

## Local Validation

Validate JSON syntax:

```bash
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
python3 -m json.tool .claude-plugin/marketplace.json >/dev/null
python3 -m json.tool plugins/zentract/.codex-plugin/plugin.json >/dev/null
python3 -m json.tool plugins/zentract/.claude-plugin/plugin.json >/dev/null
python3 -m json.tool plugins/zentract/.mcp.json >/dev/null
```

Validate the Claude plugin when Claude Code is installed:

```bash
claude plugin validate plugins/zentract
```

Validate the Codex marketplace by adding it locally:

```bash
codex plugin marketplace add /Users/lemi/code/zentract-plugins
codex plugin add zentract@zentract-plugins
```

Start a new Codex thread after reinstalling.

## Release Checklist

- [ ] Version bumped in both plugin manifests.
- [ ] Version bumped in `.claude-plugin/marketplace.json`.
- [ ] Marketplace descriptions still match the plugin behavior.
- [ ] JSON syntax validation passes.
- [ ] Claude plugin validation passes, when available.
- [ ] MCP public connectivity check returns a `tools/list` response.
- [ ] Repository is pushed to the expected GitHub remote.
