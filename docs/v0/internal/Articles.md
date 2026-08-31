---
created: 2026-08-14T16:44:32.355Z
updated: 2026-08-31T15:50:02.000Z
outline:
  pageWidth: full
---


<!-- outline:block id="tbl_2d8943d4-7c17-4e" type="table" version="2" -->
```outline-config
title: Articles
columns:
  - id: column_1
    dataType: text
    inputType: text
  - id: column_8
    dataType: text
    inputType: text
  - id: column_5
    dataType: option
    inputType: select
    defaultValue: Pending
    meta:
      options:
        - Pending
        - In Progress
        - Completed
        - On Hold
        - Archived
      allowOptionCreation: true
  - id: column_7
    dataType: text
    inputType: note
  - id: column_4
    dataType: text
    inputType: note
  - id: column_2
    dataType: text
    inputType: text
  - id: column_3
    dataType: option
    inputType: select
    meta:
      options:
        - Internal
        - Public
      allowOptionCreation: true
  - id: column_6
    dataType: option
    inputType: select
    meta:
      options:
        - Resource Items
        - AI
        - Terminal
        - Tables
        - Excalidraw
        - Html
        - Workflows
        - Spaces
        - Notes
        - Advanced
      allowOptionCreation: true
view:
  columnWidths:
    column_8: 194
    column_5: 122
    column_7: 103
  columnLineLimits:
    column_8: 3
  grouping:
    columnIds:
      - column_3
      - column_6
  groupOrder:
    - '["group-path",[["column_3","[\"string\",\"Public\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Internal\"]"]]]'
    - '["group-path",[["column_3","[\"empty\"]"]]]'
```

| Title | Note | Status | Notes | Page | Video | Scope | Area |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Resource Items&nbsp; |  |  |  |  | https://cap.so/s/rja2v63xhvdk8m7 | Internal | Resource Items |
| Fixing Issues with Skills and the Chat |  |  |  |  | https://cap.so/s/4p4barsmjz17d1p&nbsp; | Internal |  |
| Use Resource Items |  | Completed |  | [[docs/v0/resource-items/use-resource-items]] |  | Public | Resource Items |
| Configure Resource Items |  | Completed |  | [[docs/v0/resource-items/configure-resource-items]] |  | Public | Resource Items |
| Starting an AI Chat |  | Completed |  | [[docs/v0/ai/starting-an-ai-chat]] |  | Public | AI |
| AGENTS.md | Understand how Outline manages agent guidance and why AGENTS.md is hidden from the sidebar by default. | Completed |  | [[docs/v0/ai/agents-md]] |  | Public | AI |
| Working with AI |  | Pending | [[.unorganized/tables/tbl_2d8943d4-7c17-4e/Untitled]] |  |  | Public | AI |
| Adding Skills |  | Completed |  | [[docs/v0/ai/adding-skills]] |  | Public | AI |
| AI in the Terminal |  | Completed |  | [[docs/v0/terminal/ai-in-the-terminal]] |  | Public | AI |
| MCP Server |  | Completed |  | [[docs/v0/ai/mcp-server]] |  | Public | AI |
| Connect Outline MCP to AI clients | Set up one local Outline MCP connection for Codex, Claude Code, Cursor, Claude Desktop, and other stdio clients. | Completed |  | [[docs/v0/ai/mcp-with-ai-clients]] |  | Public | AI |
| Manage MCP access for a Space | Choose Off, Read only, or Read &amp; write access for each Space shared with external AI clients. | Completed |  | [[docs/v0/ai/manage-mcp-access-for-a-space]] |  | Public | AI |
| Troubleshoot Outline MCP | Resolve connection, permission, tool-catalog, file-access, conflict, and preview issues. | Completed |  | [[docs/v0/ai/troubleshoot-outline-mcp]] |  | Public | AI |
| Link to notes | Add, open, and manage links to notes in the editor, AI Chat, and tables. | Completed |  | [[docs/v0/notes/link-to-notes]] |  | Public | Notes |
| iCloud | Learn where Outline stores new and existing Spaces, how `Main` is chosen, and when a Space appears on another Mac. | Completed |  | [[docs/v0/spaces/icloud]] |  | Public | Spaces |
| Choose where attachments are saved | Choose the folder used for new attachments and understand its independent sidebar visibility. | Completed |  | [[docs/v0/spaces/choose-where-attachments-are-saved]] |  | Public | Spaces |
| Hide files and folders from the sidebar | Hide, find, and unhide exact files, folders, and patterns while keeping them available in the Space. | Completed |  | [[docs/v0/spaces/hide-files-and-folders-from-the-sidebar]] |  | Public | Spaces |
| Configure a Space with space.json | Configure exact paths, patterns, parent visibility precedence, attachments, resources, chat, agents, and editor settings. | Completed |  | [[docs/v0/advanced/configuration]] |  | Public | Advanced |
| View and edit note frontmatter | Display, add, edit, validate, and configure YAML frontmatter in a Space. | Completed |  | [[docs/v0/mcp/view-and-edit-note-frontmatter]] |  | Public | Advanced |
| Launch a terminal session |  |  |  |  |  | Public | Terminal |
| Using Tables | A simple introduct to data tables | Pending |  | [[docs/v0/tables/using-tables]] |  | Public | Tables |
| Create and edit Excalidraw drawings | A brief simple intro to excalidraw type files in outline. <br><br>How to create a new file.&nbsp; | Completed |  | [[docs/v0/excalidraw/create-excalidraw-drawings]] |  | Public | Excalidraw |
|  |  |  |  |  |  | Public |  |
|  |  |  |  |  |  | Public |  |
|  |  |  |  |  |  |  |  |
|  |  | Pending |  |  |  | Public | Html |
| Use Excalidraw with AI agents | Should explain how excalidraw inoutline can be handled by ai agents. <br><br>Should start by explain ghtat that ai agents can work with excalidraw drawings in outline through the mcp server. <br><br>Then the first example should be how to work with excalidraw and the ai agentin side outline ai chat. <br><br>Then a section explaining how external ai clients can work with excalidrawin draginw in outline like codex, claude, cursor. <br><br>At the end we can add links to learn more about the mcp server and learn more about how ai agents work.&nbsp; | Completed |  | [[docs/v0/excalidraw/excalidraw-with-ai-agents]] |  | Public | Excalidraw |
|  |  | Pending |  |  |  | Public | Html |
|  |  | Pending |  |  |  | Public | Terminal |
| Table data types | A detailed overview of all the column data types with a usage screenshot of each type | Pending |  |  |  | Public | Tables |
|  |  | Pending |  |  |  | Public | Tables |
| Managing Projects with AI | Turn a customer project request into a well-scoped task by asking AI to capture the needed details and attach the original inquiry. | Pending |  | [[docs/v0/workflows/managing-projects-with-ai]] |  | Public | Workflows |
| Turning Customer Emails into Tasks | Use AI to extract customer context and next steps from an email, then create an assigned task with the source attached. | Pending |  | [[docs/v0/workflows/turning-customer-emails-into-tasks]] |  | Public | Workflows |
| Planning a Product Launch | Use a shared launch plan to organize milestones, ownership, reference material, and follow-up tasks in one place. | Pending |  | [[docs/v0/workflows/planning-a-product-launch]] |  | Public | Workflows |
| Running Weekly Team Meetings | Keep weekly meetings focused by turning agendas, decisions, and action items into a reusable team workflow. | Pending |  | [[docs/v0/workflows/running-weekly-team-meetings]] |  | Public | Workflows |
<!-- /outline:block -->
