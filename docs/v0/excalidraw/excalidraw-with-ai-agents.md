---
created: 2026-08-18T16:00:11+02:00
updated: 2026-10-11T18:14:34.558Z
---
AI agents can create, inspect, preview, and update Excalidraw drawings in an Outline Space through Outline MCP. Creating a drawing through MCP requires **Outline tools 0.0.2 or later**. Name the drawing or its path and describe what you want.

<!-- outline:block id="img_f4dd497c-eba" type="image" version="1" assetId="Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" src="Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" alt="Copy of Motivational Quote Gradient Desktop Wallpaper 1.png" -->
![Copy of Motivational Quote Gradient Desktop Wallpaper 1.png](<Attachments/Copy of Motivational Quote Gradient Desktop Wallpaper 1.png>)
<!-- /outline:block -->

## Use Outline AI Chat

Outline AI Chat is connected to the current Space automatically.

1. Open the Space and start an AI chat.
2. Choose **Ask** when you only want to inspect or preview a drawing.
3. Choose **Agent** when you want the AI to create or change a drawing.
4. Name the drawing or include its path in your request, then describe what you want.

For example:

> Create `API flow.excalidraw` at the Space root, showing a client, API server, and database.

> Preview `Diagrams/API flow.excalidraw`.

> Update `Diagrams/API flow.excalidraw` with a database and an error-handling path.

Ask mode cannot make changes. If you request creation or an update while the chat is in Ask mode, switch to Agent mode and ask again. When creating a file inside a folder, that folder must already exist. If the returned validation reports errors after saving, the agent should repair the saved drawing.

## Use an external AI client

You can also connect Outline MCP to [Codex](https://openai.com/codex/), [Claude](https://www.anthropic.com/claude), [Cursor](https://cursor.com/), or another client that supports local MCP servers.

Enable the Space under **Settings &gt; Space &gt; AI MCP access**:

- **Read only** lets the client search, read, and preview drawings without changing them.
- **Read &amp; write** also lets the client create drawings and update existing ones with Outline tools 0.0.2 or later.

One external MCP connection can work with all enabled Spaces. If more than one Space is enabled, name the Space and drawing in your request so the agent chooses the right one.

Only enable **Read &amp; write** for clients you trust. To configure a client, see [Connect Outline MCP to AI clients](/docs/v0/ai/mcp-with-ai-clients).

## Related articles

- [MCP tools reference](/docs/v0/mcp/tools-reference)
- [Manage MCP access for a Space](/docs/v0/ai/manage-mcp-access-for-a-space)
- [About the Outline MCP server](/docs/v0/ai/mcp-server)
- [Start an AI chat](/docs/v0/ai/starting-an-ai-chat)

