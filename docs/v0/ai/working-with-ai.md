---
description: Work with Outline notes in local AI apps and Outline's built-in Chat.
---
AI can help you find, summarize, and update notes. Outline stores notes as files on your Mac, so you can work with them in a local AI app or use Chat inside Outline.

## Work with external AI agents

For an app that can access local folders, open your Space folder as its working folder. The app reads the files directly, subject to its own permissions and settings. You can find a Space folder from the Space selector: open its **…** menu and select **Show in Finder** or **Copy Path**.

For an AI client that supports a **local stdio MCP server**, connect [Outline MCP](</docs/v0/ai/mcp-with-ai-clients>) and set [MCP access for each Space](</docs/v0/advanced/manage-mcp-access-for-a-space>). This gives the client Outline's search, reading, preview, and supported file tools without making its working folder the Space. MCP access starts **Off**. Direct folder access and MCP are separate ways to work with the same local notes; the Space's MCP access setting controls only MCP.

<!-- outline:block id="youtube_ec428731-73d" type="youtube" version="1" src="https://www.youtube.com/watch?v=Ewbdtv4shhw" title="Watch — youtube.com" -->
[Watch — youtube.com](https://www.youtube.com/watch?v=Ewbdtv4shhw)
<!-- /outline:block -->

For a command-line agent, you can also [work from Outline's Terminal](</docs/v0/ai/ai-in-the-terminal>). Start a terminal in the Space so the agent uses that folder as its working directory. The agent itself must already be installed and signed in.

## Give the AI useful context

Name the Space and the note or folder you want it to use, and say what result you need. For example: “Read `Today.md`, group the unfinished tasks by priority, and suggest a short plan. Do not edit the note yet.” Start with a question or draft when you want to inspect the result before changes.

In Outline Chat, use the composer **+** menu to add the current note, another note, a folder, or reusable content. See [Add context and reusable content](</docs/v0/ai/add-context-and-reusable-content>) for the available groups. For a local agent working with files, you can give it the note or folder path. In an MCP client, name the Space and file; the client can find it with Outline tools.

When a precise location matters, use **Copy link** on selected text or on a table or row in the note. You can paste that reference into a Chat message. For external agents, a note or folder path is often more useful; right-click the item in the sidebar and select **Copy Path**.

## Review changes

Ask for a proposed edit or summary first. If you allow an agent to write, check the changed note in Outline: confirm facts, links, table values, and formatting before relying on it. In Outline Chat, **Ask** inspects content without editing; **Agent** can make changes.

## Related articles

- [Set up AI Chat](</docs/v0/ai/set-up-ai-chat>)
- [Start an AI chat](</docs/v0/ai/starting-an-ai-chat>)
- [Connect Outline MCP to AI clients](</docs/v0/ai/mcp-with-ai-clients>)

