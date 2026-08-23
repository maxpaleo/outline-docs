---
created: 2026-08-18T00:01:39+02:00
updated: 2026-08-20T23:04:14.535Z
---
# About the Outline MCP server

Outline MCP lets a compatible AI client work with notes and files in the Outline Spaces you approve. MCP stands for Model Context Protocol, a standard that allows an AI client to use tools supplied by another application.

## How it works

The AI client starts the Outline MCP server as a local process. One connection can work with every Space you have enabled under **Settings &gt; Space &gt; AI MCP access**.

The server communicates directly with the client and does not open a network port. It stops when the client closes its connection, and it can work while Outline is closed as long as the enabled Space folders remain available on your Mac.

When more than one Space is enabled, the client can use `list_spaces` to choose the right one. This list contains only each Space's name, ID, and access level. It does not reveal the Space's location on disk.

## Choose an access level

Every Space starts with external MCP access set to **Off**.

**Read only** lets an external client:

- Search notes.
- Read a note.
- List a folder.
- Preview a supported file.

**Read &amp; write** also lets an external client:

- Create folders and Markdown notes.
- Update Markdown notes.
- Update existing Excalidraw drawings.

Give **Read &amp; write** access only to clients you trust. Your AI client may still ask for approval before it runs a tool.

Turning access **Off** or reducing it takes effect on the next tool call. After enabling a Space or increasing its access, you may need to reconnect the MCP server so the client refreshes its available tools.

These settings affect external MCP clients only. Outline's built-in AI Chat uses its own Ask and Agent modes.

## Space boundaries

Every tool path is relative to the selected Space. The server rejects paths outside that Space and does not follow symbolic links.

Excluded files remain unavailable. Hidden files are omitted from normal searches and folder listings unless the client specifically includes them. Locked note contents are never decrypted for the MCP client.

## Changes and conflicts

Before updating an existing note or drawing, the client must read its current revision. If the file changes before the update is saved, Outline returns a conflict instead of overwriting the newer version. The client can then read the file again before trying another update.

## Previews

Outline MCP can return visual previews for supported local files. Markdown and HTML previews do not run scripts or load remote content. Excalidraw drawings are rendered in an isolated, time-limited process.

Some formats, including PDFs, may be returned as a local file reference instead of a rendered image. What appears in the conversation also depends on the image and resource content supported by the AI client.

## Data and privacy

Outline MCP does not add telemetry, cloud storage, or an HTTP connection. Searches, reads, and previews use files in an enabled Space and return requested content to the connected AI client.

The AI client may process that content according to its own settings and privacy policy. Review those settings before enabling access to private Spaces.

## Related articles

- [[Help Center/Public/AI/MCP with AI Clients|Connect Outline MCP to AI clients]]
- [[Help Center/Public/AI/Manage MCP access for a Space|Manage MCP access for a Space]]
- [[Help Center/Public/AI/Troubleshoot Outline MCP|Troubleshoot Outline MCP]]

