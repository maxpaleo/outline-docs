This is working evidence for the approved `docs/v0` restructure. It records what the current local source and demo files show; it is not a claim that these behaviors were manually verified in a released build. Compare affected steps and screenshots with the intended released macOS app during article review.

## Settled editorial decisions

- The answers in [[docs/v0/internal/Temp/New Doc Structure QA]] cover questions 01–27. Answer 27 allows screenshot placeholders in working article files and requires the requested screenshots to be added before push. Do not push or publish placeholders.
- The beginner journey uses the Space provided on first launch, then note creation, selection formatting, and `/` insertion. Space creation and AI setup have separate guides.
- Use the demo Space read-only. `/Users/max/Desktop/My Space/Today.md` contains a short introductory paragraph, Morning/Afternoon/Later sections, and simple tasks. Its text is a suitable consistent example for Get Started and Writing and formatting; avoid copying its personal names or internal task instructions into public copy. The existing table screenshots use a Café renovation scenario, which can remain a separate table example if the surrounding text matches.

## Product source evidence for article writers

<!-- outline:block id="tbl_a5407dcb-dd0e-4e" type="table" version="1" -->
```outline-config
columns:
  - id: topic
    dataType: text
    inputType: text
  - id: current_local_observation
    dataType: text
    inputType: text
  - id: source
    dataType: text
    inputType: text
view:
  columnWidths:
    current_local_observation: 253
    source: 377
```

| Topic | Current local observation | Source |
| --- | --- | --- |
| Default Space | Startup ensures a default local Space. New users can begin with that Space; the source does not require a create-Space step first. | `/Users/max/Code/outline/apps/mac-os/src/services/spaces/space-startup-service.ts`; `/Users/max/Code/outline/apps/mac-os/src/services/spaces/space-service.ts` (`ensureDefaultLocalSpace`) |
| Create a note | The macOS UI has **New note** in the main view and **New Note** in sidebar creation menus; the tab button is labeled **Create note**. Use the label matching the screenshot/context. | `/Users/max/Code/outline/apps/mac-os/src/ui/views/main-view.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/sidebar/sidebar-space-actions.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/tabs/document-tabs.tsx` |
| Formatting and insertion | The editor toolbar includes Bold and Italic actions. The editor command menu recognizes `/` typed at the current selection. | `/Users/max/Code/outline/packages/outline-editor-2/src/components/toolbar/outline-editor-2-toolbar.tsx`; `/Users/max/Code/outline/packages/outline-editor-2/src/components/command-menu/commands.ts`; `/Users/max/Code/outline/packages/outline-editor-2/src/components/command-menu/outline-editor-2-command-menu.tsx` |
| Spaces | The space selector lists Spaces for switching and has **New Space**. Its dialog offers **Create new** and **Use existing folder**; new Spaces can use **iCloud** or **This Mac** where available. Confirm the exact open-window behavior when writing steps. | `/Users/max/Code/outline/apps/mac-os/src/ui/components/sidebar/space-selector.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/sidebar/space-list-items.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/sidebar/space-create-dialog.tsx` |
| PDF export | A note menu exposes **Export as PDF…**. The dialog prepares and shows a PDF preview, displays **A4 portrait**, and saves with **Export**. It exports a single note snapshot. The UI lists PDF export as a Pro feature. | `/Users/max/Code/outline/apps/mac-os/src/ui/components/editor/note-controls-menu-items.tsx`; `/Users/max/Code/outline/apps/mac-os/src/features/note-pdf-export/note-pdf-export-dialog.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/plan/plan-presentation.ts` |
| PDF limits and rendering | Current source stops export beyond 4 MiB of Markdown or 100 images, among other image budgets. Unavailable images receive visible placeholders. Keep public limitations brief and task-relevant; verify plan gating and rich-content behavior against the released app. | `/Users/max/Code/outline/apps/mac-os/src/services/notes/note-pdf-limits.ts`; `/Users/max/Code/outline/apps/mac-os/src/features/note-pdf-export/README.md`; `/Users/max/Code/outline/apps/mac-os/src/services/notes/note-pdf-document.ts` |
| Built-in AI Chat | The AI settings page exposes Codex connection settings. The connection flow says **Enable Codex in Outline**, then offers account sign-in methods; it may show **Waiting for ChatGPT sign-in…** and **Open sign-in page**. Setup states may differ, so describe the branch the reader actually sees. | `/Users/max/Code/outline/apps/mac-os/src/ui/components/settings/pages/ai-page.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/ai-chat/ai-connection-panel.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/ai-chat/ai-connection-dialog.tsx` |
| Copy references | The editor supports **Copy link** for selected text and structural table/row targets; its table header exposes **Copy link**. The macOS note editor forwards these requests to its structural-link handler. Confirm the exact note and folder menu labels separately before publishing reference instructions. | `/Users/max/Code/outline/packages/outline-editor-2/src/components/context-menus/selection-menu-items.tsx`; `/Users/max/Code/outline/packages/outline-editor-2/src/tiptap/table/table-header.tsx`; `/Users/max/Code/outline/packages/outline-editor-2/src/tiptap/table/table-node-view.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/components/editor/note-editor.tsx`; `/Users/max/Code/outline/apps/mac-os/src/ui/hooks/use-outline-structural-links.ts` |
| Templates | Existing usage and configuration articles already cover the two distinct tasks. Review UI labels, paths, and screenshots during their article pass. | `docs/v0/notes/create-a-note-from-a-template.md`; `docs/v0/advanced/add-and-edit-templates.md` |
| Docs assets | Root `docs/v0/meta.json` has `attachmentsDir: "Attachments"`. The docs parser explicitly permits `attachmentsDir` at the version root, and navigation retains it; preserve that existing setting while changing navigation. | `docs/v0/meta.json`; `/Users/max/Code/outline/apps/outline-docs/lib/docs/docs-schemas.ts`; `/Users/max/Code/outline/apps/outline-docs/lib/docs/docs-navigation.ts` |
<!-- /outline:block -->

## Validation still needed before push

- The sources above are local code evidence, not a deployed manual check. Review release parity for steps, PDF Pro availability, rich elements, and AI setup before marking articles complete.
- Verify external-app connection paths individually before claiming support. Avoid inferring that all clients use the same MCP setup.
- The current docs app's legacy Markdown normalization only converts its exact Help Center/Public wiki prefix. Existing `[[docs/v0/...]]` public cross-article links need working web-route links during the restructure; keep internal tracker wiki links in the required managed-note format. Source: `/Users/max/Code/outline/apps/outline-docs/lib/docs/legacy-docs-markdown.ts`.
- Parent visual review found the current first-use, formatting, command-menu, and three table screenshots suitable when text aligns. Inspect each referenced visual again when substantially editing its article. Add all required replacement/new screenshots before push.

## Superseded Get Started visual

The generic welcome-note image was removed from the first-note steps so the requested current `Today` capture can show the actual creation result without a redundant image. Its managed block and asset remain here for provenance; it should not be used as evidence of the note-creation controls.

<!-- outline:block id="img_96acefcf-3f4" type="image" version="1" assetId="Attachments/welcome-to-outline-light 1.png" src="Attachments/welcome-to-outline-light 1.png" alt="Welcome note in Outline" -->
![Welcome note in Outline](<Attachments/welcome-to-outline-light 1.png>)
<!-- /outline:block -->

## Part 4 source checks

- The macOS New space dialog has **Type** choices **Create new** and **Use existing folder**. A new Space has **Location** choices **iCloud** and **This Mac**; the existing-folder branch uses **Choose folder** and **Create**. The Space selector lists Spaces for switching, and the per-Space menu offers **Open in New Window** and **Show in Finder**. Sources: `apps/mac-os/src/ui/components/sidebar/space-create-dialog.tsx`, `space-list-item.tsx`, `space-action-items.tsx`.
- The built-in Codex connection card offers **Set up Codex** when the runtime or tools are absent, **Retry setup** after a failed setup, and **Enable Codex in Outline** only when installed but disabled. Signed-out state offers available account methods; pending state says **Waiting for ChatGPT sign-in…** and can show **Open sign-in page** and a code. It reaches **Connected** after sign-in. Sources: `apps/mac-os/src/ui/components/ai-chat/codex-connection-settings.tsx` and `ai-connection-panel.tsx`.
- The Chat/Terminal workspace header shows a **+** menu next to its tabs, and an empty workspace shows the same menu centrally. Its actions include **New Chat** and **New Terminal**. Sources: `apps/mac-os/src/ui/components/workspace-pages/workspace-page-surface.tsx` and `workspace-page-picker.tsx`. The editor has **Copy link** for selected text, tables and rows; sidebar file/folder menus use **Copy Path**. These are different references. Sources: `packages/outline-editor-2/src/components/context-menus/selection-menu-items.tsx`, `table-header.tsx`, `table-node-view.tsx`, and macOS sidebar context menus.
- External-client setup reviewed against [official Codex MCP docs](https://learn.chatgpt.com/docs/extend/mcp?surface=cli), [Claude Code MCP docs](https://code.claude.com/docs/en/mcp), [Cursor MCP docs](https://cursor.com/docs/mcp), and [Claude Desktop local MCP guide](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop). Codex CLI and Cursor local stdio paths are supported; Claude Desktop also has a local MCP path. No generic ChatGPT macOS local stdio path is claimed.
- Part 4 new article screenshots still required before push: the macOS New space dialog with Type/Location; the Settings &gt; AI Codex card in first-install and signed-out sign-in states. Text placeholders are in those articles. The already tracked Get Started and PDF captures remain outstanding.

