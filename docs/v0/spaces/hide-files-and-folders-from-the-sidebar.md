---
description: Hide or unhide files and folders while keeping them available in your Space.
updated: 2026-08-31T15:50:02.000Z
---
You can keep files and folders available in Outline while hiding them from a Space's sidebar.

Hidden items remain available to search, links, open tabs, and AI agents. Hiding a folder also hides everything inside it.

## Hide a file or folder

1. Right-click the file or folder in the sidebar.
2. Select **Hide**.

Outline adds the exact path to the Space's visibility settings. If you rename or move the item in Outline, its visibility setting moves with it.

## View and unhide hidden items

To temporarily display every hidden item, open **Settings** at the bottom of the sidebar and select **Show Hidden Items**. Hidden items display an eye-off icon.

Right-click a hidden item and select **Unhide** to make it visible normally. Select **Hide Hidden Items** when you no longer want hidden content displayed.

## Manage exact paths and patterns

1. Open the Space selector.
2. Select **Advanced**.
3. Under **Hidden from Sidebar**, select an exact path or pattern to hide or show it.

A checked item is hidden. An unchecked item is visible. Select **Hide all** or **Show all** to change every item displayed in the menu at once.

If a folder is hidden, everything inside it stays hidden even when a child path is set to visible. Unhide the parent folder to show its visible children.

## Add or edit patterns

1. Open the Space selector.
2. Select **Advanced**, then **Settings**.
3. Under **Content visibility**, add one glob pattern per line:
   - **Hidden patterns** stay available in the Space but do not normally appear in the sidebar.
   - **Excluded patterns** are not indexed, searchable, or available to agents.
4. Select **Save**.

A pattern cannot be both hidden and excluded. Exclusions are intended for content Outline should not discover at all, such as repository metadata. Excluded paths and patterns do not appear under **Hidden from Sidebar**.

Changing the attachment folder does not automatically add or update a visibility rule.

## Related articles

- [[docs/v0/spaces/choose-where-attachments-are-saved]]
- [[docs/v0/advanced/configuration]]
