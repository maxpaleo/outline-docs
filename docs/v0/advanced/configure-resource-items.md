---
created: 2026-08-16T18:32:13.000Z
updated: 2026-08-28T17:59:55.927Z
---
Configure reusable file groups for each Space in `.outline/space.json`. For example, you can make a folder of prompts or Terminal commands appear in the resource menu. Space settings show the current setup under **File sources** and **Providers**.

Outline always supplies **Notes and folders** and **Context**. New Spaces also have file groups for **Templates** and **Commands**, but you can rename, reorder, disable, remove, or add file groups. A group finds Markdown (`.md`) files in the Space using paths you choose.

## Configure a file group

Open the Space’s `.outline/space.json` file and edit its `discovery` array.

> To find `space.json` quickly:
>
> Open **Space settings → Resource discovery → Show in Finder**, then open `space.json` in a text editor.



For example, this entry creates a group for a “Prompts” folder:

```json
{
  "id": "project-prompts",
  "title": "Prompts",
  "description": "Reusable prompts for this Space.",
  "paths": [".my-resources/prompts/**/*.md"],
  "tags": ["kind:prompt"],
  "enabled": true
}
```



<!-- outline:block id="tbl_dc38fa6d-fade-42" type="table" version="2" -->
```outline-config
title: Resource Group Keys
columns:
  - id: column_1
    dataType: text
    inputType: text
  - id: column_2
    dataType: text
    inputType: text
  - id: column_3
    dataType: text
    inputType: text
view:
  columnWidths:
    column_1: 132
    column_2: 138
```

| Key | Type | Description |
| --- | --- | --- |
| id | string | A unique ID for the group. |
| title | string | The name shown in resource menus. |
| description | string | A short description of the group. |
| paths | array of strings | Glob patterns matching Markdown files in the Space. |
| tags | array of strings | Tags used to describe and categorize the resources. |
| enabled | boolean | Whether Outline discovers and displays the group’s files. |
<!-- /outline:block -->



Add the entry as another object inside the existing `discovery` array. Each matching Markdown file becomes a resource item. The **Prompts** screenshot above shows what the new group can look like in Chat.

## Add a Terminal command

To make command files appear in the Terminal resource menu, configure a file group that discovers them. New Spaces include a **Commands** group for `.outline/commands/**/*.md`; if your Space does not have one, add an entry like this to its `discovery` array:

```json
{
  "id": "outline-commands",
  "title": "Commands",
  "description": "Reusable Terminal commands for this Space.",
  "paths": [".outline/commands/**/*.md"],
  "tags": ["kind:command"],
  "enabled": true
}
```

Then create a Markdown file such as `.outline/commands/start-claude.md` in that Space:

```markdown
---
title: Start Claude
description: Start Claude Code in the current working directory.
outline:
  command:
    mode: run
---
claude
```

The Markdown body is the command sent to Terminal. By default, selecting a command inserts it for review. The `mode: run` setting makes it run when selected. Use that setting only for commands you want to run immediately.



## Related articles

- [Add skills to AI Chat](</docs/v0/ai/adding-skills>)
- [Use AI in the Terminal](</docs/v0/ai/ai-in-the-terminal>)
- [Add context and reusable content](</docs/v0/ai/add-context-and-reusable-content>)

