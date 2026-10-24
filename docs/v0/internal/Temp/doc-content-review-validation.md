Follow-up on 2026-10-24: the two Excalidraw guides were combined into [[docs/v0/notes/excalidraw]], covering creation, editing, and AI agents. Both screenshots were retained. Navigation and tracker entries now use the combined article; the earlier validation snapshot below predates this merge. The current public inventory is 36 articles, with 32 visible and four Workflows drafts hidden. The combined article rendered through the current docs app pipeline with both images; navigation and search each contain 32 visible articles, all 92 public cross-links resolve, both old Notes routes return 404, and the merged note and tracker have no managed Markdown errors.

The approved comments in [[.unorganized/tables/tbl_1f9fdb27-70a/Untitled 3]] are implemented locally. Nothing has been committed, pushed, merged, or deployed. Content and navigation checks passed; final screenshots and a walkthrough in the intended released macOS build remain before publication.

## Changes from the review

- Elements now uses Core/More sections, individual element headings, short descriptions, native list/checklist/quotation examples, and the retained code-block screenshot.
- Tables lists column inputs as bullets without storage-type detail, repeated Link/Image URL explanations, or the legacy paragraph.
- Templates has a selection-dialog screenshot brief. Excalidraw AI focuses on drawing requests and uses the same example path throughout, linking to setup instead of repeating Chat modes and MCP access instructions.
- Attachment locations, MCP access, and MCP troubleshooting moved into Advanced. All public links and tracker Page fields use their new paths; essential MCP access steps remain in the connection guide.
- Sidebar hiding is a short Spaces guide with the supplied GIF. Exact paths, patterns, and exclusions are covered by the new Manage file visibility guide under Advanced.
- Lock and unlock notes is a new Spaces guide with the supplied GIF. It distinguishes note locks from the app-wide vault, documents the Pro requirement and current lack of password recovery, and explains that Markdown remains readable outside Outline.
- AI articles use simpler introductions and a precise Codex agent harness reference. The Terminal introduction focuses on starting an installed agent; command authoring lives in Configure resource items. Default resource groups are listed as examples, with customizable file groups distinguished from built-in Notes and folders/Context. The warnings section was removed.
- Navigation uses concise labels while frontmatter retains descriptive page titles. Related articles use short bullet lists where useful. Existing screenshot briefs are now managed image placeholders with unique IDs.
- The signed-out Terminal screenshot was replaced by a capture brief. Its original file is unchanged, and its original managed image block is archived below.

The public inventory is now 37 Markdown articles: 33 visible articles and four hidden Workflows drafts. Internal notes remain hidden. Article tracking and the Docs Content Changes task summary link to this note; the task remains In Progress while capture and release checks are pending.

## Product and image checks

Instructions were checked against the current local source in `/Users/max/Code/outline`:

- `apps/mac-os/src/ui/components/sidebar/space-actions-submenu.tsx`: exact menu paths are **Advanced → Space Settings** and **Advanced → Sidebar Visibility**; the latter contains exact-path/pattern checkboxes and a conditional Hide all/Show all action.
- `apps/mac-os/src/ui/components/settings/space-settings-panel.tsx`: the Attachments folder field saves with Return or its checkmark. Changing it affects new attachments only. Hidden and excluded pattern controls are separate.
- `apps/mac-os/src/services/outline-services.ts`, `services/vault/vault-service.ts`, `ui/components/vault/vault-passphrase-dialog.tsx`, `ui/hooks/note-lock-action.ts`, and `services/notes/note-types.ts`: app-wide vault configuration, note/vault controls, password-recovery limitation, Pro gating for locking, and readable Markdown files.
- `apps/mac-os/src/services/resources/resource-discovery-config.ts` and `ui/components/settings/space-resource-discovery-settings.tsx`: default Templates/Commands file groups, configurable discovery sources, built-in Notes and folders/Context, and the optional Codex Skills provider.

Retained images in substantially edited articles were inspected. The supplied 720p hiding and locking GIFs were inspected across their timelines and copied byte-for-byte into `Attachments/hiding-files-folders.gif` and `Attachments/locking-notes.gif`. Their SHA-256 hashes match the supplied originals. The captions describe what each actually demonstrates; neither claims to show password setup.

An independent content/cleanup review found two issues: outdated submenu names and inconsistent Excalidraw prompt paths. Both were fixed and independently rechecked. No further actionable findings remain from that review.

## Validation performed

Temporary scripts outside the content repository used the current application's real local filesystem service, article parser, navigation schemas, search projection, sitemap function, and shared MarkdownServer renderer. They used explicit local configuration without GitHub credentials or content requests.

- Parsed and rendered all 33 visible articles; generated 33 search documents and 33 v0 sitemap entries. No metadata warnings or broken rendered local article links/heading fragments were found.
- Confirmed all 12 currently hidden articles return 404 through the service. Hidden articles are excluded from search and sitemap. Confirmed the three newly retired routes return 404 and their replacements resolve.
- Loaded all 16 distinct rendered local image assets through the local asset service, including the two GIFs and the shared placeholder image.
- Validated managed Markdown across `docs/v0`: all six managed tables parse, with no error diagnostics or duplicate block IDs. The article/task tables retain their schemas and stable column IDs.
- Verified navigation metadata references existing direct children, every tracker row has eight cells, and tracker note/Page links resolve. Exactly ten public rows remain In Progress for screenshot work.
- Compared the work against a snapshot taken before this revision: original image assets, `docs/v1`, answered Q&A, and the user's review comments are unchanged. No application code, dependencies, environment files, or generated build output were added to this content repository. `git diff --check` passes.
- Inspected the actual Next.js docs app at `localhost:3011`: Elements hierarchy/examples, short sidebar labels, new locking guide and GIF, Advanced article placement, attachment configuration example/placeholder, and resource guide rendering. Full-text search for “vault” found the new guide and navigated to its `#lock-a-note` section.

No application build or broad application test suite was run for this content-only change. These checks do not establish parity with the intended released macOS build or exercise production GitHub/cache invalidation; those remain separate from local article rendering.

## Required captures before push

There are 11 placeholder image blocks across these ten articles. Set up AI Chat has two distinct states.

| Working article | Capture needed |
| --- | --- |
| [[docs/v0/get-started]] | A new Today note selected in the macOS sidebar, with its title and a few lines of text. |
| [[docs/v0/notes/create-a-note-from-a-template]] | Template selection modal showing Global, This space, a selected template, and Create. |
| [[docs/v0/notes/export-a-note-as-a-pdf]] | Loaded PDF preview with A4 portrait and Export. |
| [[docs/v0/spaces/create-and-manage-spaces]] | New space dialog with Create new and the iCloud/This Mac location choices. |
| [[docs/v0/advanced/choose-where-attachments-are-saved]] | Space Settings → General → Attachments folder with an example relative path and checkmark save control. |
| [[docs/v0/ai/set-up-ai-chat]] | Codex first-install Set up Codex state, then the ChatGPT sign-in state. |
| [[docs/v0/ai/starting-an-ai-chat]] | One active in-app conversation with composer, resource button, Ask/Agent selector, and model selector. |
| [[docs/v0/ai/working-with-ai]] | A verified external Codex session updating a named Outline note through MCP, with request and result. |
| [[docs/v0/ai/add-context-and-reusable-content]] | Composer resource menu with default groups and a reusable item where practical. |
| [[docs/v0/ai/ai-in-the-terminal]] | Replacement image with an installed, signed-in agent ready in Outline Terminal, using an example Space and no private paths. |

Replace each placeholder with its final screenshot, remove its capture brief, and inspect the finished article. Verify the relevant procedures in the intended released macOS build before push. The supplied hiding/locking GIFs are already present; they do not need placeholder replacements.

Current route mapping: [[docs/v0/internal/Temp/doc-url-migration]]. The earlier restructuring checkpoint is retained in [[docs/v0/internal/Temp/doc-restructure-validation]].

## Superseded Terminal image

The original asset is retained. It shows Claude Code signed out and a development-file reference, so the public Terminal article now requests a replacement screenshot of a signed-in agent. This original managed block is archived here for reference.

<!-- outline:block id="img_6f3fa77b-082" type="image" version="1" assetId="Attachments/claude-code-in-terminal.png" src="Attachments/claude-code-in-terminal.png" alt="Claude Code open in Outline's Terminal beside a note" -->
![Claude Code open in Outline's Terminal beside a note](Attachments/claude-code-in-terminal.png)
<!-- /outline:block -->
