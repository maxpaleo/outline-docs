---
created: 2026-08-18T00:01:39+02:00
updated: 2026-08-28T17:58:17.032Z
---
# Connect Outline MCP to AI clients

Connect Outline MCP once to let Codex, Claude Code, Cursor, or another compatible AI client work with the Spaces you approve. The connection runs locally on your Mac and does not open a network port.

Outline's built-in AI Chat is configured automatically. Follow this guide only when connecting an external client.

## Before you begin

1. Install Outline in your Applications folder.
2. In Outline, open each Space you want to share and go to **Settings &gt; Space**.
3. Under **AI MCP access**, choose **Read only** or **Read &amp; write**.
4. Go to **Settings &gt; AI** and confirm that the Outline MCP server is available.

New and existing Spaces start with MCP access set to **Off**. You do not need a separate MCP connection for each Space.

## Codex

In Outline, go to **Settings &gt; AI** and select **Copy Codex setup command**. Paste the command into Terminal and run it.

The command looks like this when Outline is installed in its default location:

```sh
codex mcp add outline -- '/Applications/Outline Notes.app/Contents/MacOS/outline-mcp'
```

Start a new Codex session after running the command. Use `/mcp` in Codex or run `codex mcp list` in Terminal to check the connection.

See [Codex MCP documentation](https://developers.openai.com/codex/mcp/) for more ways to manage MCP servers.

## Claude Code

In Outline, go to **Settings &gt; AI** and select **Copy Claude Code setup command**. Paste the command into Terminal and run it.

The command looks like this when Outline is installed in its default location:

```sh
claude mcp add --scope user outline -- '/Applications/Outline Notes.app/Contents/MacOS/outline-mcp'
```

Start a new Claude Code session after running the command. Use `/mcp` in Claude Code or run `claude mcp list` in Terminal to check the connection.

See [Claude Code MCP documentation](https://code.claude.com/docs/en/mcp) for more configuration options.

## Cursor

Add Outline to your global Cursor MCP configuration at `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "outline": {
      "type": "stdio",
      "command": "/Applications/Outline Notes.app/Contents/MacOS/outline-mcp",
      "args": []
    }
  }
}
```

Restart Cursor, then open **Customize &gt; MCP** to confirm that Outline is connected. A global configuration makes the same Outline tools available across your Cursor projects.

See [Cursor MCP documentation](https://cursor.com/docs/mcp) for project-specific configuration and other options.

## Claude Desktop and other clients

Clients that support local stdio MCP servers commonly accept an `mcpServers` JSON entry:

```json
{
  "mcpServers": {
    "outline": {
      "type": "stdio",
      "command": "/Applications/Outline Notes.app/Contents/MacOS/outline-mcp",
      "args": []
    }
  }
}
```

Add this entry using your client's MCP settings or configuration file, then restart or reconnect the client. The exact configuration location depends on the client.

Outline only copies setup commands. It never changes another app's configuration.

## Check the connection

Try a request such as:

> List the Outline Spaces you can access.

Then ask the client to work with a specific Space:

> In my Work Space, list the notes and folders at the root.

If only one Space is enabled, the client can usually select it automatically. If more than one Space is enabled, the client uses `list_spaces` to find the correct Space.

Other example requests include:

- “Find my notes about the launch plan.”
- “Read `Projects/Status.md` and summarize it.”
- “Preview `Drawings/System.excalidraw`.”
- “Create a note called Meeting Notes in the Projects folder.”
- “Update the project status note with these changes.”

Creating or updating content requires **Read &amp; write** access and may still require approval in your AI client.

After enabling another Space or changing a Space from **Read only** to **Read &amp; write**, reconnect the MCP server or start a new client session if the new tools do not appear. Turning access **Off** or reducing it takes effect immediately.

## Related articles

- [[docs/v0/ai/manage-mcp-access-for-a-space]]
- [[docs/v0/ai/troubleshoot-outline-mcp]]
- [[docs/v0/ai/mcp-server]]

