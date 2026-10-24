---
description: Manage which Space files appear in the sidebar or are excluded from Outline.
---
Control which files appear in your sidebar with exact paths and patterns. Hidden items remain available to search, links, open tabs, and AI agents. Excluded items are not indexed, searchable, or available to agents.

## Manage existing rules

1. Open the Space selector and select **Advanced → Sidebar Visibility**.
2. Select an exact path or pattern to change its visibility. Checked items are hidden; unchecked items are visible.
3. Select **Hide all** to hide every item in the menu. When all are hidden, select **Show all** to show them.

Excluded paths and patterns do not appear in this menu. If a folder is hidden, everything inside it stays hidden even when a child path is set to visible. Show the parent folder to reveal its visible children.

## Add or edit patterns

1. Open the Space selector and select **Advanced → Space Settings**.
2. Under **Content visibility**, enter one glob pattern per line in **Hidden patterns** or **Excluded patterns**.
3. Select **Save**.

Use **Hidden patterns** for content you want to keep available in Outline without showing it in the sidebar. Use **Excluded patterns** for content Outline should not discover at all. A pattern cannot be both hidden and excluded.

A glob pattern matches several paths. For example, `**/Drafts` matches folders named `Drafts` anywhere in the Space.

## Related articles

- [Hide files and folders from the sidebar](/docs/v0/spaces/hide-files-and-folders-from-the-sidebar)
- [Configure a Space with space.json](/docs/v0/advanced/configuration)
