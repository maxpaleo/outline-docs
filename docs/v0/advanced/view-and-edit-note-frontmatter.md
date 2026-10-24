---
title: "View and edit note frontmatter"
created: 2026-08-26T18:51:02Z
updated: 2026-08-26T22:16:02.153Z
---
Frontmatter is optional YAML metadata stored at the beginning of a Markdown note. You can use it for dates, statuses, custom fields, and other structured information.

## Show or hide frontmatter

1. Open a note and select **Note actions** in the top-right corner.
2. Select **Show Frontmatter**.

This setting applies to every note in the current Space. Select it again to hide frontmatter. Hiding frontmatter does not remove it from your notes.

<!-- outline:block id="img_cd26cb6b-4ea" type="image" version="1" assetId="Attachments/show-frontmatter.png" src="Attachments/show-frontmatter.png" alt="show-frontmatter.png" -->
![show-frontmatter.png](Attachments/show-frontmatter.png)
<!-- /outline:block -->

## Add or edit frontmatter

<!-- outline:block id="img_88d86c9e-92b" type="image" version="1" assetId="Attachments/edit-frontmatter.png" src="Attachments/edit-frontmatter.png" alt="edit-frontmatter.png" -->
![edit-frontmatter.png](Attachments/edit-frontmatter.png)
<!-- /outline:block -->

When a note has no frontmatter, select **Add frontmatter** below its title. Enter YAML using keys and values, for example:

```yaml
status: active
category: research
```

To edit existing frontmatter, click inside the frontmatter block and make your changes. The Cancel and Save buttons appear after the content changes:

- Select **Cancel** to discard your changes.
- Select **Save** to update the note.

If the YAML is invalid, Outline adds a warning icon and highlights the frontmatter block. Hover over the warning to see the problem. Fix the YAML before saving.

## Change the syntax colors

1. Open the current Space's settings.
2. Under **Editor**, find **Frontmatter syntax colors**.
3. Choose **Muted** or **Standard**. Muted is the default.

You can also show or hide frontmatter for the Space using **Show note frontmatter** in the same section.

## Related articles

- [Configure a Space with space.json](</docs/v0/advanced/configuration>)

