# claude-code

## Garmin MCP

`.mcp.json` registers the [garmin_mcp](https://github.com/Taxuspt/garmin_mcp) server for Claude Code.
It runs locally only (requires `uv`). Credentials are read from your shell environment — never commit them:

```bash
export GARMIN_EMAIL="you@example.com"
export GARMIN_PASSWORD="..."
claude   # approve the "garmin" project MCP server when prompted
```

The first run may ask for an MFA code; tokens are cached locally afterwards.
