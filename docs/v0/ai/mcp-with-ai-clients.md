---
created: 2026-08-18T00:01:39+02:00
updated: 2026-10-11T18:14:34.558Z
---
Connect Outline MCP once to let Codex, Claude Code, Cursor, or another compatible AI client work with the Spaces you approve. The connection runs locally on your Mac and does not open a network port.

Outline's built-in AI Chat is configured automatically. Follow this guide only when connecting an external client.

## Before you begin

1. Install Outline.
2. In Outline, open each Space you want to share and go to **Settings &gt; Space**.
3. Under **AI MCP access**, choose **Read only** or **Read &amp; write**.
4. Go to **Settings > AI > Outline tools**. Select **Install Outline tools** if needed, or use **Repair** from the tools menu. Wait for **External setup available**.

New and existing Spaces start with MCP access set to **Off**. You do not need a separate MCP connection for each Space.

## Codex

In Outline, go to **Settings > AI > Outline tools**, open the tools menu, and select **Copy Codex setup command**. Paste the command into Terminal and run it.

The command has this form. Use the actual path copied from Outline:

```sh
codex mcp add outline -- '/absolute/path/from-outline/Runtimes/OutlineMcp/bin/outline-mcp'
```

Start a new Codex session after running the command. Use `/mcp` in Codex or run `codex mcp list` in Terminal to check the connection.

See [Codex MCP documentation](https://developers.openai.com/codex/mcp/) for more ways to manage MCP servers.

## Claude Code

In Outline, go to **Settings > AI > Outline tools**, open the tools menu, and select **Copy Claude Code setup command**. Paste the command into Terminal and run it.

The command has this form. Use the actual path copied from Outline:

```sh
claude mcp add --scope user outline -- '/absolute/path/from-outline/Runtimes/OutlineMcp/bin/outline-mcp'
```

Start a new Claude Code session after running the command. Use `/mcp` in Claude Code or run `claude mcp list` in Terminal to check the connection.

See [Claude Code MCP documentation](https://code.claude.com/docs/en/mcp) for more configuration options.

## Cursor

Add Outline to your global Cursor MCP configuration at `~/.cursor/mcp.json`. Replace the example `command` with the actual executable path from an Outline setup command:

```json
{
  "mcpServers": {
    "outline": {
      "type": "stdio",
      "command": "/absolute/path/from-outline/Runtimes/OutlineMcp/bin/outline-mcp",
      "args": []
    }
  }
}
```

Restart Cursor, then open **Customize &gt; MCP** to confirm that Outline is connected. A global configuration makes the same Outline tools available across your Cursor projects.

See [Cursor MCP documentation](https://cursor.com/docs/mcp) for project-specific configuration and other options.

## Claude Desktop and other clients

Clients that support local stdio MCP servers commonly accept an `mcpServers` JSON entry. Replace the example `command` with the actual executable path from an Outline setup command:

```json
{
  "mcpServers": {
    "outline": {
      "type": "stdio",
      "command": "/absolute/path/from-outline/Runtimes/OutlineMcp/bin/outline-mcp",
      "args": []
    }
  }
}
```

Add this entry using your client's MCP settings or configuration file, then restart or reconnect the client. The exact configuration location depends on the client.

Outline only copies setup commands. It never changes another app's configuration. The managed executable path stays the same across tools updates. If you previously configured a command inside `Outline Notes.app`, replace it with the copied managed command.

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

## Keep Outline tools up to date

The file tools require **Outline tools 0.0.2 or later**. Update Outline to a version that supports them, then install or repair the tools under **Settings > AI > Outline tools**. Updating the app does not automatically upgrade the installed tools when it opens. Reconnect the client after a tools update.

## Related articles

- [MCP tools reference](/docs/v0/mcp/tools-reference)
- [Manage MCP access for a Space](/docs/v0/ai/manage-mcp-access-for-a-space)
- [Troubleshoot Outline MCP](/docs/v0/ai/troubleshoot-outline-mcp)
- [About the Outline MCP server](/docs/v0/ai/mcp-server)

