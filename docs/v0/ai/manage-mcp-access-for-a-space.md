---
created: 2026-08-21T00:57:13+02:00
updated: 2026-08-28T17:57:48.758Z
---
# Manage MCP access for a Space

Choose which Outline Spaces an external AI client can use and whether it can make changes. Access is managed separately for every Space and starts **Off**.

## Change a Space's access

1. Open the Space in Outline.
2. Open **Settings &gt; Space**.
3. Under **AI MCP access**, choose an access level.

The available levels are:

- **Off** — External AI clients cannot access the Space.
- **Read only** — Clients can list folders, search, read, validate, and preview accessible content.
- **Read &amp; write** — Clients can also create folders and supported notes, and update supported notes and drawings.

These settings affect external MCP clients such as Codex, Claude Code, and Cursor. They do not change what Outline's built-in AI Chat can do.

## After changing access

Turning access **Off** or changing **Read &amp; write** to **Read only** takes effect immediately, including for clients that are already connected.

After enabling a Space or increasing access to **Read &amp; write**, reconnect the Outline MCP server or start a new client session if the Space or write tools do not appear.

If a Space is disconnected or its folder is unavailable on your Mac, external clients cannot use it until it becomes available again.

## What remains protected

MCP access does not bypass Outline's existing protections:

- Locked note contents are not shared.
- Excluded files are unavailable.
- Symbolic links are not followed.
- Updates require the latest file revision, which prevents an older client response from overwriting newer changes.
- Your AI client may require a separate approval before running a tool.

## Related articles

- [[docs/v0/ai/mcp-with-ai-clients]]
- [[docs/v0/ai/mcp-server]]
- [[docs/v0/ai/troubleshoot-outline-mcp]]

