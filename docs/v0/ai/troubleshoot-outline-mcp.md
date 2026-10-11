---
created: 2026-08-21T00:57:13+02:00
updated: 2026-10-11T18:14:34.558Z
---
Use these checks when an external AI client cannot connect to Outline or cannot use the expected tools.

## The Outline MCP server is unavailable

Open **Settings > AI > Outline tools** in Outline. Select **Install Outline tools** if they are missing, or **Repair** from the tools menu if the installation needs repair. Retry setup if a download fails.

If your client uses an old command pointing inside the app bundle, install the tools, then replace its setup with the command copied from the tools menu. The managed command works independently of the app bundle location.

## The client cannot connect

1. Open **Settings &gt; AI** in Outline.
2. Under **Outline tools**, open the menu and copy the setup command for Codex or Claude Code. Run it, or update your client's MCP configuration with the executable path in that command.
3. Restart the client or begin a new session.
4. Check the client's MCP server list and confirm that `outline` is enabled and connected.

Outline MCP is a local stdio server. It does not use a URL, port, login, or API key.

## No Outline Spaces are available

Open each Space you want to share, then go to **Settings &gt; Space &gt; AI MCP access** and choose **Read only** or **Read &amp; write**.

A Space also needs to remain connected and its folder must be available locally on your Mac. After enabling a new Space, reconnect the client if it still does not appear.

## Write tools are missing

Set the Space's **AI MCP access** to **Read &amp; write**, then reconnect the MCP server or start a new client session. Some clients cache the tool list from when they first connect.

Your client may also require approval before it can run a write tool.

## A newly added tool is missing

The file tools require **Outline tools 0.0.2 or later**. Update Outline to a version that includes support for them, then open **Settings > AI > Outline tools** and install or repair the tools as needed. Updating the app does not automatically upgrade the tools when it opens.

Reconnect the MCP server or start a new client session afterward. Some clients cache the available tools. Version 0.0.1 has the previous note tools; the new file tools do not provide aliases for them. See [MCP tools reference](/docs/v0/mcp/tools-reference).

The `get_agent_docs` tool does not require Space access. It returns only Outline's built-in agent guidance, not notes or files from a Space.

## The client asks for a Space ID

Ask the client to call `list_spaces` and choose the Space by name. When more than one Space is enabled, pass the selected Space's returned `id` as `spaceId` to Space tools.

## A note or file is unavailable

Check whether the item is:

- Locked.
- Excluded from the Space.
- Behind a symbolic link.
- Stored in a folder that is not currently available on your Mac.
- Hidden from normal search and folder results.

Hidden items can be included in search or folder listings when the client explicitly requests them.

## An update reports a conflict

The file changed after the client last read it. Ask the client to read the latest version and try the update again. Outline does not overwrite a newer revision automatically.

## A write reports validation errors

Check whether the result contains `saved: true`. If it does, the file was saved even though the content has errors. Ask the agent to correct that file with `update_file` using its returned revision, then validate it again. Do not ask it to create the file again.

`not_supported` means no validator exists for the format. `unavailable` means a supported check could not run; it does not undo a successful save.

## A preview is not shown as an image

The file format or AI client may not support an inline visual preview. Some previews are returned as a local resource instead. Try opening the referenced file in Outline.

## Related articles

- [MCP tools reference](/docs/v0/mcp/tools-reference)
- [Connect Outline MCP to AI clients](/docs/v0/ai/mcp-with-ai-clients)
- [Manage MCP access for a Space](/docs/v0/ai/manage-mcp-access-for-a-space)
- [About the Outline MCP server](/docs/v0/ai/mcp-server)

