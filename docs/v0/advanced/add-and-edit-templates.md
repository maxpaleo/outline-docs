---
title: Add and edit templates
description: Configure reusable Markdown templates for every Space on your Mac or for one Space.
keywords:
  - templates
  - global templates
  - space templates
  - configuration
---
Use any saved Markdown note as a template in Outline for macOS. Give it a friendly title and an optional description, then add its file path to your template configuration.

## Add a global template

Global templates are available in every Space on this Mac.

1. Open the sidebar **+** menu and select **From template**.
2. Select **Open configuration file** to open or locate `outline.json`.
3. Save your template as a `.md` file. You can use the `Templates` folder beside `outline.json` or another folder on your Mac.
4. In a text editor, add an entry to the configuration's `templates` array and save the file.

For example:

```json
{
  "templates": [
    {
      "title": "Project brief",
      "description": "Goals, scope, and next steps for a project.",
      "path": "Templates/project-brief.md"
    }
  ]
}
```

Preserve any existing entries and other settings. `title` and `path` are required; `description` is optional.

A relative path such as `Templates/project-brief.md` starts from the folder containing `outline.json`. To use a file elsewhere, enter its full path, such as `/Users/your-name/Documents/Outline Templates/project-brief.md`.

Global templates are local to this Mac and are not automatically synced to other devices.

## Add a template for one Space

Save the template inside the Space, then add a `templates` array to its existing `.outline/space.json`. Preserve the file's other settings and any existing templates.

This property belongs inside the existing JSON object:

```json
"templates": [
  {
    "title": "Weekly review",
    "description": "Review this project's progress.",
    "path": "Templates/weekly-review.md"
  }
]
```

Space paths start from the Space's root folder, rather than `.outline`. They must stay inside that Space; absolute paths and `..` are not supported.

For help finding and editing the file, see [[docs/v0/advanced/configuration|Configure a Space with space.json]].

## Edit or remove a template

Open the source `.md` file, make your changes, and save it. Future notes use the latest saved content; existing copies stay unchanged. The starter templates in the global `Templates` folder are editable too.

To change a template's displayed title or description, edit its configuration entry. If you move or rename the source file, update its `path`.

To remove a template from the selector, remove its entry from the array. This does not delete the source note. Removed starter templates are not automatically restored.

Only files listed in the configuration appear in the selector. Adding a file to the `Templates` folder alone does not register it.

## Reload templates and resolve access

After saving configuration changes, return to Outline or select **Reload templates**. If the selected entry changed, select it again before creating a note.

If Outline cannot access an external global template, select **Grant access…**, choose the folder containing the file, then try **Create** again. Outline remembers access on this Mac; you may need to grant it again if access expires or is revoked.

Use literal `.md` file paths. Web addresses, `~`, environment variables, and wildcard patterns are not supported. If a template is unavailable, check its path and the error shown in the dialog.

## Related articles

- [[docs/v0/notes/create-a-note-from-a-template|Create a note from a template]]
