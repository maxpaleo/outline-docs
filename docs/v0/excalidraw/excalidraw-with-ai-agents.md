---
created: 2026-08-18T16:00:11+02:00
updated: 2026-08-28T17:59:28.354Z
---
# Use Excalidraw with AI agents

AI agents can inspect, preview, and update existing Excalidraw drawings in an Outline Space through the Outline MCP server. Create the drawing in Outline first, then tell the agent which drawing you want to work with.

<!-- outline:block id="img_f4dd497c-eba" type="image" version="1" assetId="Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" src="Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" alt="Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" -->
![Copy of Motivational Quote Gradient Desktop Wallpaper 1.png](<Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png>)
<!-- /outline:block -->

## Use Outline AI Chat

Outline AI Chat is connected to the current Space automatically.

1. Open the Space and start an AI chat.
2. Choose **Ask** when you only want to inspect or preview a drawing.
3. Choose **Agent** when you want the AI to change a drawing.
4. Name the drawing or include its path in your request, then describe what you want.

For example:

> Preview `Diagrams/API flow.excalidraw`.

> Update `Diagrams/API flow.excalidraw` with a database and an error-handling path.

Ask mode cannot make changes. If you request an update while the chat is in Ask mode, switch the chat to Agent mode and ask again.

## Use an external AI client

You can also connect Outline MCP to [Codex](https://openai.com/codex/), [Claude](https://www.anthropic.com/claude), [Cursor](https://cursor.com/), or another client that supports local MCP servers.

Enable the Space under **Settings &gt; Space &gt; AI MCP access**:

- **Read only** lets the client search, read, and preview drawings without changing them.
- **Read &amp; write** also lets the client update existing drawings.

One external MCP connection can work with all enabled Spaces. If more than one Space is enabled, name the Space and drawing in your request so the agent chooses the right one.

Only enable **Read &amp; write** for clients you trust. To configure a client, see [[docs/v0/ai/mcp-with-ai-clients]].

## Related articles

- [[docs/v0/ai/manage-mcp-access-for-a-space]]
- [[docs/v0/ai/mcp-server]]
- [[docs/v0/ai/starting-an-ai-chat]]

