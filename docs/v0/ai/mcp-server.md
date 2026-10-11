---
created: 2026-08-18T00:01:39+02:00
updated: 2026-10-11T18:14:34.558Z
---
Outline MCP lets a compatible AI client work with notes and files in the Outline Spaces you approve. MCP stands for Model Context Protocol, a standard that allows an AI client to use tools supplied by another application.

## How it works

The AI client starts the Outline MCP server as a local process. One connection can work with every Space you have enabled under **Settings &gt; Space &gt; AI MCP access**.

The server communicates directly with the client and does not open a network port. It stops when the client closes its connection, and it can work while Outline is closed as long as the enabled Space folders remain available on your Mac.

When more than one Space is enabled, the client can use `list_spaces` to choose the right one. This list contains only each Space's name, ID, and access level. It does not reveal the Space's location on disk.

## Choose an access level

Every Space starts with external MCP access set to **Off**.

**Read only** lets an external client:

- Search accessible text and binary files.
- Read text or inspect binary file metadata.
- List a folder.
- Validate saved content.
- Preview a supported file.

**Read &amp; write** also lets an external client:

- Create folders and UTF-8 text files, including Markdown, Excalidraw, HTML, JSON, and CSV.
- Update existing text files using their current revision.

These file tools require **Outline tools 0.0.2 or later**. Binary files can be discovered and inspected, but cannot be created or updated through these tools. See [MCP tools reference](/docs/v0/mcp/tools-reference) for all tools and their inputs.

Give **Read &amp; write** access only to clients you trust. Your AI client may still ask for approval before it runs a tool.

Turning access **Off** or reducing it takes effect on the next tool call. After enabling a Space or increasing its access, you may need to reconnect the MCP server so the client refreshes its available tools.

These settings affect external MCP clients only. Outline's built-in AI Chat uses its own Ask and Agent modes.

## Space boundaries

Every tool path is relative to the selected Space. The server rejects paths outside that Space and does not follow symbolic links.

Excluded files remain unavailable. Hidden files are omitted from normal searches and folder listings unless the client specifically includes them. Locked note contents are never decrypted for the MCP client.

## Changes and conflicts

Before updating an existing text file, the client must read its current revision. If the file changes before the update is saved, Outline returns a conflict instead of overwriting the newer version. The client can then read the file again before trying another update.

Creating or updating a file saves it before returning validation diagnostics. If content is malformed, the agent can correct the saved file using the returned revision. Markdown updates preserve existing frontmatter.

## Previews

Outline MCP can return visual previews for supported local files. Markdown and HTML previews do not run scripts or load remote content. Excalidraw drawings are rendered in an isolated, time-limited process.

Some formats, including PDFs, may be returned as a local file reference instead of a rendered image. What appears in the conversation also depends on the image and resource content supported by the AI client.

## Data and privacy

Outline MCP does not add telemetry, cloud storage, or an HTTP connection. Searches, reads, and previews use files in an enabled Space and return requested content to the connected AI client.

The AI client may process that content according to its own settings and privacy policy. Review those settings before enabling access to private Spaces.

## Installation and updates

Outline tools are installed separately from the app through **Settings > AI > Outline tools**. An app update specifies the required tools version, but opening it does not automatically upgrade the installed runtime. Install or repair the tools as needed, then reconnect your client.

## Related articles

- [MCP tools reference](/docs/v0/mcp/tools-reference)
- [Connect Outline MCP to AI clients](/docs/v0/ai/mcp-with-ai-clients)
- [Manage MCP access for a Space](/docs/v0/ai/manage-mcp-access-for-a-space)
- [Troubleshoot Outline MCP](/docs/v0/ai/troubleshoot-outline-mcp)

