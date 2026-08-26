---
created: 2026-08-16T18:32:13.000Z
updated: 2026-08-26T22:26:06.539Z
---
# Configure resource items

Resource groups are configured separately for each Space in `.outline/space.json`. Space settings show the current configuration in two read-only sections: **File sources** and **Providers**.

File-backed resource items are Markdown (`.md`) files that can be stored anywhere in a Space. To configure them, open the Space’s `.outline/space.json` file and update the `discovery` array.

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



<!-- outline:block id="img_7c033259-9bd" type="image" version="1" assetId="Attachments/prompts.png" src="Attachments/prompts.png" alt="prompts.png" -->
![prompts.png](Attachments/prompts.png)
<!-- /outline:block -->



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



Add the entry as another object inside the existing `discovery` array. Each matching Markdown file becomes a resource item.



## Related articles

- [[Help Center/Public/AI/Adding Skills|Add skills to AI Chat]]
- [[Help Center/Public/Terminal/AI in the Terminal|Use AI in the Terminal]]

