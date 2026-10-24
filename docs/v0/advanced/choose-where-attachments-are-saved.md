---
title: "Choose where attachments are saved"
description: Choose the folder where a Space saves new attachments.
updated: 2026-08-31T15:50:02.000Z
---
Each Space can use its own folder for images and other files you add to notes. The default folder is `Attachments`.

## Change the folder in Settings

1. Open the Space selector and select **Advanced → Space Settings**.
2. Under **General**, find **Attachments folder**.
3. Enter a path relative to the Space, such as `Media/Uploads`.
4. Press Return or select the checkmark in the field to save it.

<!-- outline:block id="img_2ce39a45-4c9" type="image" version="1" assetId="Attachments/attachment-location.png" src="Attachments/attachment-location.png" alt="attachment-location.png" -->
![attachment-location.png](Attachments/attachment-location.png)
<!-- /outline:block -->

Outline creates the folder when you add the first attachment to it.

## Change the folder in space.json

Open the Space's `.outline/space.json` file and set `attachments.directory` to a folder path relative to the Space:

```json
{
  "attachments": {
    "directory": "Media/Uploads"
  }
}
```

Keep the rest of the file intact and save valid JSON. For help finding and editing the file, see [Configure a Space with space.json](</docs/v0/advanced/configuration>).

## Existing attachments and visibility

Changing the folder affects new attachments only. Outline does not move existing files or update their paths. Existing attachments continue to open from their original locations.

The new folder may appear in the sidebar. Its visibility is controlled separately.

## Related articles

- [Hide files and folders from the sidebar](</docs/v0/spaces/hide-files-and-folders-from-the-sidebar>)
- [Manage file visibility](</docs/v0/advanced/manage-file-visibility>)

