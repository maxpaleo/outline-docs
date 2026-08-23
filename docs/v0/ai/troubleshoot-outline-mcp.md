---
created: 2026-08-21T00:57:13+02:00
updated: 2026-08-21T22:00:05.530Z
---
# Troubleshoot Outline MCP

Use these checks when an external AI client cannot connect to Outline or cannot use the expected tools.

## The Outline MCP server is unavailable

Open **Settings &gt; AI** in Outline and check the server status under **External AI apps**.

If Outline reports that its bundled MCP server is unavailable, reinstall the latest version of Outline. If you moved or reinstalled the app, copy and run the setup command again so your client uses the current executable path.

## The client cannot connect

1. Open **Settings &gt; AI** in Outline.
2. Copy the setup command for Codex or Claude Code and run it again, or update your client's MCP configuration with the displayed executable path.
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

After updating Outline, reconnect the MCP server or start a new client session. Some clients keep the tool list from when they first connected, so tools included in a newer Outline version may not appear until the connection is refreshed.

The `get_agent_docs` tool does not require Space access. It returns only Outline's built-in agent guidance, not notes or files from a Space.

## The client asks for a Space ID

Ask the client to call `list_spaces` and choose the Space by name. When more than one Space is enabled, note tools need the ID returned for the selected Space.

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

## A preview is not shown as an image

The file format or AI client may not support an inline visual preview. Some previews are returned as a local resource instead. Try opening the referenced file in Outline.

## Related articles

- [[Help Center/Public/AI/MCP with AI Clients|Connect Outline MCP to AI clients]]
- [[Help Center/Public/AI/Manage MCP access for a Space|Manage MCP access for a Space]]
- [[Help Center/Public/AI/MCP Server|About the Outline MCP server]]

