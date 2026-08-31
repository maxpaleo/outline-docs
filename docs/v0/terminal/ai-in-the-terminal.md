---
created: 2026-08-16T22:22:52.000Z
updated: 2026-08-28T18:00:10.127Z
---
# Use AI in the Terminal

Outline’s Terminal composer uses the same resource groups as Chat and can start supported AI coding agents.

<!-- outline:block id="img_6f3fa77b-082" type="image" version="1" assetId="Attachments/claude-code-in-terminal.png" src="Attachments/claude-code-in-terminal.png" alt="claude-code-in-terminal.png" -->
![claude-code-in-terminal.png](Attachments/claude-code-in-terminal.png)
<!-- /outline:block -->

1. Open a Terminal in the current Space.
2. Type `/` or select the **+** button and open **Commands**.
3. Choose a command such as **Start Codex**, **Start Claude**, or **Start Cursor Agent**.

New Outline-managed Spaces include starter command files for these agents. Existing and external Spaces show the commands configured in their resource settings instead.

## Add a command

Commands are Markdown files, usually stored in `.outline/commands`.

The Markdown body contains the text sent to the Terminal. Commands insert their text by default, so you can review it before pressing Return.

To run a command as soon as you select it, set `outline.command.mode` to `run` in its frontmatter:

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

Configured skill folders also appear in the resource menu. Selecting a file-backed skill inserts the shell-safe path to the selected skill file. Selecting a skill from **Codex Skills** inserts it in its `$skill-name` format.

Use `$skill-name` only inside a Codex session. At a normal shell prompt, the shell treats it as a variable.

To add a skills folder, see [[docs/v0/ai/adding-skills]].