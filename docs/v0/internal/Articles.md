---
created: 2026-08-14T16:44:32.355Z
updated: 2026-10-11T18:14:34.558Z
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
        - Excalidraw
        - Html
        - Workflows
        - Spaces
        - Notes
        - Advanced
        - Get Started
        - Introduction
        - Elements
        - macOS
      allowOptionCreation: true
view:
  columnWidths:
    column_8: 164
    column_5: 99
    column_7: 103
    column_3: 118
    column_6: 121
  columnLineLimits:
    column_8: 3
    column_6: 2
  grouping:
    columnIds:
      - column_3
      - column_6
  collapsedGroupKeys:
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"AI\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Terminal\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Resource Items\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Excalidraw\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Html\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Workflows\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Spaces\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Advanced\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"empty\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Internal\"]"],["column_6","[\"string\",\"Resource Items\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Notes\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Public\"]"],["column_6","[\"string\",\"Get Started\"]"]]]'
  groupOrder:
    - '["group-path",[["column_3","[\"string\",\"Public\"]"]]]'
    - '["group-path",[["column_3","[\"string\",\"Internal\"]"]]]'
    - '["group-path",[["column_3","[\"empty\"]"]]]'
```

| Title | Note | Status | Notes | Page | Video | Scope | Area |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Documentation restructuring plan | Initial restructure and follow-up content review implemented locally: 32 visible articles and four hidden Workflows drafts. Ten articles await final screenshot captures or replacement; current validation is linked from the plan. | In Progress | [[docs/v0/internal/Temp/New Doc Structure QA]] | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 1]] |  | Internal |  |
| Introduction | Introduces local notes, macOS/iOS availability, and optional AI work. | Completed |  | [[docs/v0/intro]] |  | Public | Introduction |
| Introduction (v1) | Replaced the v1 scaffold with a pending-documentation notice and a link to v0. Page title, sidebar, and breadcrumb use Introduction. | Completed |  | [[docs/v1/index]] |  | Public | Introduction |
| Create and manage Spaces | Creation/switching guide retained with shorter Spaces navigation label and link to locking. Capture New Space dialog before push. | In Progress | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 1]] | [[docs/v0/spaces/create-and-manage-spaces]] |  | Public | Spaces |
| Set up AI Chat | Codex agent harness wording updated; capture first-install and sign-in states before push. | In Progress | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 1]] | [[docs/v0/ai/set-up-ai-chat]] |  | Public | AI |
| Export a note as a PDF | PDF export steps and preview drafted; capture the macOS export-dialog screenshot described in the article before push. | In Progress | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 1]] | [[docs/v0/notes/export-a-note-as-a-pdf]] |  | Public | Notes |
| Resource Items&nbsp; |  |  |  |  | https://cap.so/s/rja2v63xhvdk8m7 | Internal | Resource Items |
| Fixing Issues with Skills and the Chat |  |  |  |  | https://cap.so/s/4p4barsmjz17d1p&nbsp; | Internal |  |
| Add context and reusable content | Plain introduction, default-group bullets, customizable file groups distinguished from built-ins; capture the resource menu before push. | In Progress |  | [[docs/v0/ai/add-context-and-reusable-content]] |  | Public | AI |
| Configure Resource Items | File-group configuration and Terminal command authoring consolidated here; no command-authoring steps in the introductory Terminal guide. | Completed |  | [[docs/v0/advanced/configure-resource-items]] |  | Public | Advanced |
| Start an AI chat | Single active-chat screenshot placeholder added; modes and setup/context links retained. Capture before push. | In Progress |  | [[docs/v0/ai/starting-an-ai-chat]] |  | Public | AI |
| AGENTS.md | Understand how Outline manages agent guidance and why AGENTS.md is hidden from the sidebar by default. | Completed |  | [[docs/v0/ai/agents-md]] |  | Public | AI |
| Working with AI | External-agent heading and change-review wording refined; capture the named-Space external-agent example before push. | In Progress | [[.unorganized/tables/tbl_2d8943d4-7c17-4e/Untitled]] | [[docs/v0/ai/working-with-ai]] |  | Public | AI |
| Add skills to AI Chat |  | Completed |  | [[docs/v0/ai/adding-skills]] |  | Public | AI |
| Use AI in the Terminal | Short agent-starting guide; command authoring moved to resource configuration. Replace signed-out Terminal screenshot before push; original block archived in review validation. | In Progress |  | [[docs/v0/ai/ai-in-the-terminal]] |  | Public | AI |
| MCP Server |  | Completed |  | [[docs/v0/ai/mcp-server]] |  | Public | AI |
| MCP tools reference | All ten tools in Outline tools 0.0.2+, with inputs, access requirements, examples, text-only writes, revisions, and advisory validation. | Completed |  | [[docs/v0/advanced/mcp-tools-reference]] |  | Public | Advanced |
| Connect Outline MCP to AI clients | Set up one local Outline MCP connection for Codex, Claude Code, Cursor, Claude Desktop, and other stdio clients. | Completed |  | [[docs/v0/ai/mcp-with-ai-clients]] |  | Public | AI |
| Manage MCP access for a Space | Moved to Advanced; essential access-enablement steps remain in the client connection guide. | Completed |  | [[docs/v0/advanced/manage-mcp-access-for-a-space]] |  | Public | Advanced |
| Troubleshoot Outline MCP | Moved to Advanced; existing troubleshooting and client setup links retained. | Completed |  | [[docs/v0/advanced/troubleshoot-outline-mcp]] |  | Public | Advanced |
| Link to notes | Add, open, and manage links to notes in the editor, AI Chat, and tables. | Completed |  | [[docs/v0/notes/link-to-notes]] |  | Public | Notes |
| iCloud | Learn where Outline stores new and existing Spaces, how `Main` is chosen, and when a Space appears on another Mac. | Completed |  | [[docs/v0/spaces/icloud]] |  | Public | Spaces |
| Choose where attachments are saved | Moved to Advanced; Settings and space.json methods documented. Capture the Attachments folder field before push. | In Progress |  | [[docs/v0/advanced/choose-where-attachments-are-saved]] |  | Public | Advanced |
| Hide files and folders from the sidebar | Short Hide/Unhide/Show Hidden Items guide with supplied GIF; exact paths and patterns moved to Advanced. | Completed |  | [[docs/v0/spaces/hide-files-and-folders-from-the-sidebar]] |  | Public | Spaces |
| Configure a Space with space.json | Configure exact paths, patterns, parent visibility precedence, attachments, resources, chat, agents, and editor settings. | Completed |  | [[docs/v0/advanced/configuration]] |  | Public | Advanced |
| View and edit note frontmatter | Display, add, edit, validate, and configure YAML frontmatter in a Space. | Completed |  | [[docs/v0/advanced/view-and-edit-note-frontmatter]] |  | Public | Advanced |
| Launch a terminal session | Covered by Use AI in the Terminal; standalone proposal archived. | Archived |  |  |  | Public | AI |
| Create Excalidraw drawings | Merged into Excalidraw; creation and editing steps and the current drawing screenshot are retained there. | Archived |  | [[docs/v0/notes/excalidraw]] |  | Public | Notes |
|  |  |  |  |  |  | Public |  |
|  |  |  |  |  |  | Public |  |
|  |  |  |  |  |  |  |  |
|  | Unnamed proposal deferred for this release. | On Hold |  |  |  | Public | Html |
| Use Excalidraw with AI agents | Merged into Excalidraw; drawing prompts, the AI example screenshot, and setup links are retained there. | Archived |  | [[docs/v0/notes/excalidraw]] |  | Public | Notes |
|  | Unnamed proposal deferred for this release. | On Hold |  |  |  | Public | Html |
|  | Unnamed proposal deferred for this release. | On Hold |  |  |  | Public | Terminal |
| Tables | Column input choices use concise bullets; repetitive link/image and legacy text removed. Existing table screenshots retained. | Completed |  | [[docs/v0/notes/tables]] |  | Public | Notes |
| Managing Projects with AI | Turn a customer project request into a well-scoped task by asking AI to capture the needed details and attach the original inquiry. Hidden draft; deferred until a later release. | On Hold |  | [[docs/v0/workflows/managing-projects-with-ai]] |  | Public | Workflows |
| Turning Customer Emails into Tasks | Use AI to extract customer context and next steps from an email, then create an assigned task with the source attached. Hidden draft; deferred until a later release. | On Hold |  | [[docs/v0/workflows/turning-customer-emails-into-tasks]] |  | Public | Workflows |
| Planning a Product Launch | Use a shared launch plan to organize milestones, ownership, reference material, and follow-up tasks in one place. Hidden draft; deferred until a later release. | On Hold |  | [[docs/v0/workflows/planning-a-product-launch]] |  | Public | Workflows |
| Running Weekly Team Meetings | Keep weekly meetings focused by turning agendas, decisions, and action items into a reusable team workflow. Hidden draft; deferred until a later release. | On Hold |  | [[docs/v0/workflows/running-weekly-team-meetings]] |  | Public | Workflows |
| Get Started | First-note journey drafted; capture the new Today-note screenshot described in the article before push. Superseded welcome image block retained in internal evidence. | In Progress | [[.unorganized/tables/tbl_2d8943d4-7c17-4e/Untitled 1]] | [[docs/v0/get-started]] |  | Public | Get Started |
| Use Outline from the menu bar | Create and reopen notes and switch Spaces from the macOS menu bar; existing menu screenshot reviewed. | Completed |  | [[docs/v0/notes/the-menu-bar]] |  | Public | Notes |
|  | Unnamed proposal deferred for this release. | On Hold |  |  |  | Public | Get Started |
|  | Unnamed proposal deferred for this release. | On Hold |  |  |  | Public | Get Started |
| Formatting | Archived source; its floating-toolbar screenshot and content are in Writing and formatting. | Archived | [[.unorganized/tables/tbl_2d8943d4-7c17-4e/Untitled 2]] |  |  | Public | Notes |
| Writing and formatting | Merges Formatting and Command Menu, retaining both image blocks and adding editor and Markdown guidance. | Completed | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 1]] | [[docs/v0/notes/writing-and-formatting]] |  | Public | Notes |
| Command Menu | Archived source; slash-menu steps and screenshot are in Writing and formatting. Old route retired. | Archived |  |  |  | Public | Notes |
| Edit images | macOS annotation workflow drafted; replace the editor screenshot placeholder before publication. | In Progress |  | [[docs/v0/notes/edit-images]] |  | Public | Notes |
| Elements | Expanded into Core/More sections with element descriptions, native Markdown examples, and the retained code-block screenshot. | Completed |  | [[docs/v0/notes/elements]] |  | Public | Notes |
| Create a note from a template | Template flow retained; capture the template-selection dialog described in the article before push. | In Progress |  | [[docs/v0/notes/create-a-note-from-a-template]] |  | Public | Notes |
| Add and edit templates | Configure global and Space templates, edit source notes, reload entries, and grant folder access. | Completed |  | [[docs/v0/advanced/add-and-edit-templates]] |  | Public | Advanced |
| Lock and unlock notes | App-wide vault setup and note/vault controls verified; supplied unlocking/relocking GIF added. Locking is Pro and leaves Markdown readable in other apps. | Completed | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 3]] | [[docs/v0/spaces/lock-and-unlock-notes]] |  | Public | Spaces |
| Manage file visibility | Exact-path controls, hidden/excluded patterns, and parent visibility rules split into an advanced guide. | Completed | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 3]] | [[docs/v0/advanced/manage-file-visibility]] |  | Public | Advanced |
| Docs content revision | Approved user comments implemented locally; navigation, links, captures, and verification recorded in the linked note. Publication remains pending screenshots and released-app review. | In Progress | [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 3]] | [[docs/v0/internal/Temp/doc-content-review-validation]] |  | Internal |  |
| Excalidraw | Combined guide to creating and editing drawings and working with AI agents; both existing screenshots retained and inspected. | Completed |  | [[docs/v0/notes/excalidraw]] |  | Public | Notes |
<!-- /outline:block -->

