---
title: "Add skills to AI Chat"
created: 2026-08-16T22:22:52.000Z
updated: 2026-08-28T17:57:20.691Z
---
Skills give an AI agent instructions for a specific task. You can add a skill stored in your Space to an Outline Chat or Terminal message.

## Use a skill

1. Select **+** in the Chat or Terminal composer.
2. Open your configured **Skills** resource group and select a skill.
3. Add your request, then send it.

A Space can expose its own skill files through resource discovery. For example, a group can show Markdown files from `.my-resources/skills`. The exact folder and group name depend on your Space's configuration.

<!-- outline:block id="img_94541083-f4b" type="image" version="1" assetId="Attachments/skill-discovery 1.png" src="Attachments/skill-discovery 1.png" alt="skill-discovery 1.png" -->
![skill-discovery 1.png](<Attachments/skill-discovery 1.png>)
<!-- /outline:block -->

## Codex Skills

When the Codex provider is enabled, its available skills appear in a separate **Codex Skills** group in Chat and Terminal. Selecting one adds its `$skill-name` reference. You can show or hide this group with the `providers.codexSkills.enabled` setting in [Space configuration](</docs/v0/advanced/configuration>).

## Related articles

- [Configure resource items](</docs/v0/advanced/configure-resource-items>)
- [Add context and reusable content](</docs/v0/ai/add-context-and-reusable-content>)

