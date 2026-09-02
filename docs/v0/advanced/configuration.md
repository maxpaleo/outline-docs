---
description: Understand and edit the advanced settings stored in a Space's configuration file.
updated: 2026-09-01T15:22:41.040Z
---
Every Space contains a `.outline/space.json` file. Outline uses this JSON file to identify the Space and store settings that travel with it.

Most common settings can be changed in **Space selector → Advanced → Settings**. Edit `space.json` directly when you need to configure options that are not available in the app.

## Before editing the file

Open **Space settings → Resource discovery**, select the actions menu, then select **Show in Finder**. Open `space.json` in a text editor.

Keep the file as valid JSON and preserve fields you are not changing. Outline detects saved changes automatically. If the file becomes invalid, Outline shows a recovery notice so you can reveal the file or restore the last valid configuration.

## Space identity

Outline manages these fields:

- `schemaVersion` identifies the configuration format.
- `id` uniquely identifies the Space.
- `name` stores the Space's original name.
- `label`, when present, provides a custom display name.
- `createdAt` and `updatedAt` record configuration timestamps.

Avoid changing `schemaVersion`, `id`, or the timestamps manually.

## Files

`files.paths` stores rules for exact Space-relative paths. `files.patterns` applies rules to every matching path:

```json
{
  "files": {
    "paths": {
      "Attachments": "hidden",
      "Projects/Plan.md": "visible"
    },
    "patterns": {
      "AGENTS.md": "hidden",
      "**/AGENTS.md": "hidden",
      "**/.git": "excluded",
      "**/TABLE_NOTES": "hidden",
      "**/.unorganized": "hidden"
    }
  }
}
```

- `visible` shows matching content in the sidebar and keeps the rule available in the in-app visibility menu.
- `hidden` removes matching content from the sidebar but keeps it indexed and available to search, links, tabs, and agents.
- `excluded` prevents matching content from being indexed, searched, or used by agents.

Use exact paths for individual files and folders. Outline updates these rules when you select **Hide** or **Unhide** from an item's context menu and carries any remaining exact rule with an item when it is moved or renamed in Outline.

Patterns support `*` within one path segment, `?` for one character, and `**` as a complete segment spanning multiple folders. Use them when the same rule should apply to several locations.

An excluded or hidden parent folder is a boundary for its entire subtree. A visible child does not appear while its parent is hidden. An exact visible rule can override a hidden pattern for the item itself when its parent folders are visible. Excluded rules take precedence over hidden and visible rules.

New Spaces hide `Attachments`, `AGENTS.md`, `.outline`, `TABLE_NOTES`, and `.unorganized` content by default. They exclude common repository metadata such as `.git`, `.obsidian`, and `.DS_Store`. `TABLE_NOTES` and `.unorganized` must remain either `visible` or `hidden` so Outline can continue to manage their content.

Excluded content is not displayed in the in-app visibility menu. Use exclusions only for content Outline should not index or discover.

For the in-app controls, see [[docs/v0/spaces/hide-files-and-folders-from-the-sidebar]].

## Attachments

`attachments.directory` sets the Space-relative folder used for new attachments:

```json
{
  "attachments": {
    "directory": "Media/Uploads"
  }
}
```

Use a folder path relative to the Space. Do not use an absolute path, `..`, glob characters, or a path inside `.outline`. Changing this value does not move existing attachments or add a file visibility rule.

For the in-app controls, see [[docs/v0/spaces/choose-where-attachments-are-saved]].

## Resource discovery

`discovery` defines groups of files that Chat and Terminal can offer as resource items. Each entry has an `id`, `title`, one or more Space-relative `paths`, optional descriptive `tags`, and an `enabled` setting.

```json
{
  "discovery": [
    {
      "id": "project-briefs",
      "title": "Project briefs",
      "description": "Briefs available in this Space.",
      "tags": ["kind:brief", "scope:space"],
      "enabled": true,
      "paths": ["Projects/**/Brief.md"]
    }
  ]
}
```

Each `id` must be unique. See [[docs/v0/resource-items/configure-resource-items]] for the complete resource discovery workflow.

## Providers

`providers` stores portable preferences for resource providers. `providers.codexSkills.enabled` controls whether Codex skills appear as a resource group:

```json
{
  "providers": {
    "codexSkills": {
      "enabled": true
    }
  }
}
```

Provider availability still depends on what is installed on the current device.

## Chat

`chat.storageMode` controls where AI chat transcripts are stored:

- `local` keeps transcripts on the current Mac.
- `space-synced` stores transcripts with the Space when that storage mode is available.

```json
{
  "chat": {
    "storageMode": "local"
  }
}
```

## Agent guide

`agentGuide.managed` controls whether Outline keeps its managed guidance in `AGENTS.md` up to date:

```json
{
  "agentGuide": {
    "managed": true
  }
}
```

Set it to `false` if you want to maintain all agent guidance yourself. See [[docs/v0/ai/agents-md]] for more about `AGENTS.md`.

## Editor

`editor` stores Space-wide editor preferences:

```json
{
  "editor": {
    "showFrontmatter": true,
    "frontmatterSyntaxTheme": "muted"
  }
}
```

- `showFrontmatter` controls whether YAML frontmatter is shown in the editor.
- `frontmatterSyntaxTheme` accepts `muted` or `default` and controls how that frontmatter is styled.

See [[docs/v0/mcp/view-and-edit-note-frontmatter]] for more about working with frontmatter.