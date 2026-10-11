---
title: MCP tools reference
description: Available Outline MCP tools, access requirements, inputs, and examples for technical users.
---
Outline MCP lets AI clients search, read, create, update, validate, and preview files in approved Spaces. This reference describes **Outline tools 0.0.2 or later**. Version 0.0.1 uses the previous note tools; the new names have no aliases for those tools.

## Access and paths

Enable a Space under **Settings &gt; Space &gt; AI MCP access**. Read only allows inspection; Read &amp; write also allows changes. Your client may ask for approval before making a change.

Call `list_spaces` to discover approved Spaces. Every Space tool accepts an optional `spaceId`; supply the `id` returned by `list_spaces` when multiple Spaces are available. The examples below omit it and assume one available Space.

Paths are relative to that Space, such as `Projects/Plan.md`. Absolute paths, paths outside the Space, symbolic links, excluded files, and locked note contents are unavailable. Search and folder listings omit hidden items unless `includeHidden` is `true`.

Tool availability depends on access when the client connects. Reconnect after enabling a Space or increasing access. Turning access Off or reducing it takes effect on the next tool call.

## Available tools

<!-- outline:block id="tbl_0ff1f4bb-9a38-4a" type="table" version="1" -->
```outline-config
columns:
  - id: tool
    dataType: text
    inputType: text
  - id: purpose
    dataType: text
    inputType: text
  - id: access
    dataType: text
    inputType: text
view:
  columnWidths:
    tool: 150
    purpose: 193
    access: 190
```

| Tool | Purpose | Access |
| --- | --- | --- |
| `list_spaces` | Discover approved Spaces and their access levels. | No Space access required |
| `get_agent_docs` | List or read built-in Outline reference documents. | No Space access required |
| `search_files` | Find files by title, filename, path, or Markdown frontmatter. | Read only |
| `read_file` | Read text and its revision, or inspect binary file metadata. | Read only |
| `list_folder` | List files and folders in one directory. | Read only |
| `preview_file` | Preview a supported file without changing it. | Read only |
| `validate_file` | Check saved content without changing it. | Read only |
| `create_folder` | Create a folder inside an existing parent. | Read &amp; write |
| `create_file` | Create a UTF-8 text file. | Read &amp; write |
| `update_file` | Replace a text file's content using its current revision. | Read &amp; write |
<!-- /outline:block -->

## Discovery and guidance

### list_spaces

Inputs: `{}`. Returns each available Space's `id`, `name`, and `access`, without its location on disk.

### get_agent_docs

Inputs: optional `doc`. Use `{}` to list document metadata, then pass a document ID to read it. Current IDs are `outline-tables` and `html-preview`.

```json
{"doc": "outline-tables"}
```

These are Outline's bundled references, not files from a Space.

## Reading and inspection

### search_files

Required: `query`. Optional: `limit` (1–100, default 20), `includeHidden` (default false).

```json
{"query": "launch", "limit": 20}
```

Search matches titles, filenames, paths, and Markdown frontmatter. Binary files can appear in results. It does not search full file bodies. Results include paths and whether the result list was truncated.

### read_file

Required: `path`.

```json
{"path": "Projects/Plan.md"}
```

Markdown returns its body, frontmatter, settings, revision, and validation results. Other text files return their source text, revision, and validation results. Malformed text remains readable so the agent can repair it. Binary files return metadata and preview guidance instead of their contents.

### list_folder

Optional: `path` (default `""`, the Space root), `limit` (1–500, default 100), `cursor`, `includeHidden` (default false).

```json
{"path": "Projects", "limit": 100}
```

Returns entries and `nextCursor`. If `nextCursor` is present, pass it as `cursor` with the same folder and options to continue listing.

### preview_file

Required: `path`. Optional: `theme` (`light`, `dark`, or `system`, default `system`), `maxWidth` (default 1200), `maxHeight` (default 900), and `page` for PDFs (starting at 1). Dimensions must be 1–4096; `page` must be 1–10000.

```json
{"path": "Diagrams/API.excalidraw", "theme": "light"}
```

Returns a rendered preview or a local resource fallback. Display depends on the file format and client. Previewing never creates or updates a file. Markdown and HTML previews do not run scripts or load remote content.

### validate_file

Required: `path`. Optional: `fileType` to select a validator for an extensionless file. For a file with an extension, `fileType` must agree with it.

```json
{"path": "Projects/Tasks.json"}
```

Checks the saved file at its current revision. Supported checks cover Markdown managed elements, Excalidraw, HTML preview compatibility, JSON syntax, and CSV structure. Validation is not a guarantee that content is correct for every other application.

## Creating and updating

### create_folder

Required: `path`. The immediate parent must exist. Calling it for an existing directory is safe.

```json
{"path": "Projects"}
```

### create_file

Required: `path`, `fileType`, and string `content`. Optional: `collisionPolicy` (`error` by default, or `increment` to choose an available numbered filename).

```json
{"path": "Projects/Tasks.json", "fileType": "json", "content": "{\"tasks\": []}"}
```

The immediate parent must exist. `fileType` is an extension such as `md`, `excalidraw`, `html`, `json`, or `csv`, rather than a MIME type. Case and one leading dot are ignored. It must agree with the path extension; aliases such as `md`/`markdown` and `html`/`htm` are accepted. The filename is not rewritten to match `fileType`. Extensionless files use `txt`.

Writes accept UTF-8 text, including other text extensions. They cannot create binary files such as PDFs, images, or XLSX workbooks, or accept base64 or artifact references as binary content.

For Markdown, `content` is the note body. For Excalidraw, it is serialized drawing JSON as a string. Newly created drawing text uses Excalifont (`fontFamily: 5`) unless another font is requested.

### update_file

Required: `path`, `expectedRevision`, and string `content`. Optional: `fileType` to assert the existing format; it cannot change that format.

First call `read_file`, then use its returned revision:

```json
{"path": "Projects/Tasks.json", "expectedRevision": "revision-from-read_file", "content": "{\"tasks\": [\"Review plan\"]}"}
```

Replace `revision-from-read_file` with the actual returned value. Updates replace the full text content. Markdown updates replace only the body and preserve existing frontmatter and note settings. Excalidraw updates use serialized drawing JSON and should preserve existing text fonts.

If the file changed after it was read, the update returns a conflict. Read it again and reconcile the changes before retrying.

## Saved files and diagnostics

`create_file` and `update_file` save first, then return `saved: true`, the resulting path and revision, and validation diagnostics. Malformed content can be saved successfully. Access restrictions, unsupported binary writes, invalid inputs, and revision conflicts can still prevent a save.

Validation can report:

- `valid`: the check passed without warnings or errors.
- `warnings`: warnings without errors.
- `errors`: content needs correction.
- `not_supported`: no validator exists for this format.
- `unavailable`: a supported check could not run.

When `saved` is true, repair errors by updating the saved file with the returned revision. Do not create it again. Use `validate_file` for another check after editing. Other text formats can be saved without a dedicated validator.

## Updating Outline tools

The app specifies which tools version it requires; the runtime is installed separately. Updating the app does not automatically upgrade the tools when it opens.

Open **Settings &gt; AI &gt; Outline tools**, install or repair the tools as needed, then reconnect your external client. The managed executable path stays the same across tools updates. If your client still points inside an older app bundle, replace that setup using the command copied from Settings.

## Related articles

- [Connect Outline MCP to AI clients](</docs/v0/ai/mcp-with-ai-clients>)
- [Manage MCP access for a Space](</docs/v0/ai/manage-mcp-access-for-a-space>)
- [Troubleshoot Outline MCP](</docs/v0/ai/troubleshoot-outline-mcp>)

