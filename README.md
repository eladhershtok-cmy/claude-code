# claude-code

## Garmin MCP

`.mcp.json` registers the [garmin_mcp](https://github.com/Taxuspt/garmin_mcp) server for Claude Code.
It runs locally only (requires `uv`) and uses saved OAuth tokens — no credentials in config.

1. Authenticate once (prompts for email, password and MFA code; saves tokens to `~/.garminconnect`):

   ```bash
   uvx --python 3.12 --from git+https://github.com/Taxuspt/garmin_mcp@a2ca5fcac34524b83814fe2fcf3d479f8a75983f garmin-mcp-auth
   ```

2. Run `claude` in this repo, approve the `garmin` project MCP server, and check `/mcp` shows it connected.

Tokens last about 6 months; re-run `garmin-mcp-auth` when they expire.

### Read-only tools

`GARMIN_ENABLED_TOOLS` in `.mcp.json` is an allowlist of garmin_mcp's read-only tools (its `READ_ONLY_TOOLS`
set in `tool_annotations.py`). Tools that add, edit, delete, schedule, upload or download are not registered.
An allowlist is used rather than a denylist so that write tools added in a future upgrade stay disabled
until added here. Names not found upstream are ignored with a warning in the server log.

### Pinned version

`.mcp.json` pins garmin_mcp to commit `a2ca5fc`, the version whose `READ_ONLY_TOOLS` the allowlist was built from,
so upstream changes never run automatically. To upgrade: review the new upstream code, update the SHA after `@` in
`.mcp.json`, and re-check the allowlist against the new `tool_annotations.py`. Re-run `garmin-mcp-auth` with the same pin.
