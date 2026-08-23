---
created: 2026-08-16T22:22:52.000Z
updated: 2026-08-21T18:20:06.730Z
---
# Add skills to AI Chat

If you keep agent skills in a Space, you can make their skill files available from the Chat composer. This works with skills you use in tools such as Codex, Claude Code, or Cursor.

## Add a skills folder

Open the Space’s resource discovery configuration and add a file-backed resource group:

```json
{
  "id": "shared-skills",
  "title": "Skills",
  "description": "Skills available in this Space.",
  "paths": [".my-resources/skills/*.md"],
  "tags": ["kind:skill"],
  "enabled": true
}
```



<!-- outline:block id="img_8895f451-6cd" type="image" version="1" assetId="Attachments/adding-skills.png" src="Attachments/adding-skills.png" alt="adding-skills.png" -->
![adding-skills.png](Attachments/adding-skills.png)
<!-- /outline:block -->

The screenshot above uses `.my-resources/skills/*.md`. If your skills are stored elsewhere, update the `paths` array with matching patterns such as `.agents/skills/*/SKILL.md`, `.agents/skills/*.md`, `.codex/skills/*/SKILL.md`, `.claude/skills/*/SKILL.md`, or `.cursor/skills/*/SKILL.md`.

For more options, see [[Help Center/Public/Resource Items/Configure Resource Items|Configure resource items]].

---

> ### Codex Skills
>
> When enabled, skills supplied by the Codex provider are automatically available in the Chat and Terminal composers.
>
> You can show or hide this group with the `providers.codexSkills.enabled` preference in `.outline/space.json`.

