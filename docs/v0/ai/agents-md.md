---
created: 2026-08-21T19:15:58.000Z
updated: 2026-08-31T15:54:37.436Z
---
An `AGENTS.md` file gives AI agents useful instructions for working with the files in an Outline Space. It helps agents understand how Outline stores notes, configuration, attachments, and supported content such as tables.

## Outline-managed guidance

Outline creates an `AGENTS.md` file at the root of a Space when one is not already present. If the file already exists, Outline adds a clearly marked managed section without replacing your instructions.

Outline may update only this managed section when the app changes. You can add your own instructions anywhere outside it. Outline never deletes `AGENTS.md` and never changes `AGENTS.md` files in subfolders.

## Find AGENTS.md in the sidebar

Outline hides `AGENTS.md` files from the sidebar by default so they do not distract from your notes. They remain available to AI agents.

To display them temporarily, open **Settings** at the bottom of the sidebar and select **Show Hidden Items**. To keep them visible, open the Space selector, select **Advanced**, then uncheck the `AGENTS.md` patterns under **Hidden from Sidebar**.

## Turn off automatic updates

In **Settings &gt; Space**, turn off **Keep Outline agent guidance up to date**.

You can also set `agentGuide.managed` to `false` in `.outline/space.json`:

```json
{
  "agentGuide": {
    "managed": false
  }
}
```

Turning this setting off removes only Outline's managed section. Your `AGENTS.md` file remains in place, and your custom instructions remain unchanged. The Space continues to work normally, but AI agents may have less information about Outline-specific features.