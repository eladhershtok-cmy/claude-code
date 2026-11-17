# claude-code

## Garmin MCP

`.mcp.json` registers the [garmin_mcp](https://github.com/Taxuspt/garmin_mcp) server for Claude Code.
It runs locally only (requires `uv`) and uses saved OAuth tokens — no credentials in config.

1. Authenticate once (prompts for email, password and MFA code; saves tokens to `~/.garminconnect`):

   ```bash
   uvx --python 3.12 --from git+https://github.com/Taxuspt/garmin_mcp garmin-mcp-auth
   ```

2. Run `claude` in this repo, approve the `garmin` project MCP server, and check `/mcp` shows it connected.

Tokens last about 6 months; re-run `garmin-mcp-auth` when they expire.
