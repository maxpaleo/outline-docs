---
created: 2026-10-23T00:41:35.825Z
updated: 2026-10-23T00:41:35.825Z
---

Restructure and complete the first-release Outline documentation so readers can find a small, coherent set of useful articles. The current beginner articles contain placeholders, while several small topics have their own top-level sections. The intended result is a complete introduction and first-use guide, followed by four sections: Notes, Spaces, AI, and Advanced.

**Status: Local content implementation complete; follow-up review changes implemented, with screenshots and released-app review pending.** Answers 01–27 remain settled. The later approved content review adds two articles, moves three guides into Advanced, and updates navigation labels and screenshot briefs. Current results and the capture checklist: [[docs/v0/internal/Temp/doc-content-review-validation]]. The inventory and checkpoints below record the initial restructure; the follow-up note records subsequent changes. No commit, push, merge, or deployment has been performed.

Decision source: [[docs/v0/internal/Temp/New Doc Structure QA]]. Follow-up answers 23–27 resolve platforms, Working with AI, AI setup, PDF/template coverage, and the screenshot requirement.

Current results: [[docs/v0/internal/Temp/doc-restructure-validation]]. Independent review: [[docs/v0/internal/Temp/doc-restructure-review]]. The later checkpoints below record the completed stages; the inventory's original-path column remains historical.

## Scope and constraints

- Work on `/Users/max/Code/outline-docs/docs/v0`. Keep `docs/v1` unchanged.
- Document the latest released version available from the Outline website, without adding a version number to article copy. Use `/Users/max/Code/outline` to verify product details, checking that any relevant local changes are released before describing them as available.
- Write step-by-step instructions for macOS. Briefly mention iOS availability in Introduction or Get Started; do not add mobile walkthroughs or imply every macOS feature is available on iOS.
- This is a content-only repository. Change Markdown, article assets when needed, navigation metadata, and the internal article tracker. Do not add application code, dependencies, build output, environment files, or a new publishing system.
- Preserve existing note frontmatter, managed block IDs, asset references, and unrelated local changes. Use kebab-case for public article paths and navigation labels for readable titles. Preserve the explicitly requested internal planning and Q&A filenames.
- Keep internal planning in the existing hidden `internal` directory or outside the published version tree. Do not introduce a new `Public` folder or another documentation version.
- Keep articles brief and task-focused. Put specialist configuration and reference material in Advanced; keep short task-specific setup guides, such as Set up AI Chat, with their feature section.
- Retain useful existing content. Hide unfinished optional articles for later; remove a redundant source only after its useful content and links have been migrated.
- Separate content changes from renderer changes. Native Outline YouTube block support, redirects, routing changes, and version registration belong to the application repository and require separate work if needed.

## Decisions from the Q&A

| Topic | Implementation decision | Answers |
| --- | --- | --- |
| Readers and tone | Write for everyday note-taking, including people new to Markdown, while remaining useful to experienced users. Use plain language; introduce terms such as Markdown and AI briefly where useful. | 02 |
| Introduction | Explain that Outline is a macOS and iOS app, that notes are local files, and that it supports modern note-taking and agent workflows. Keep the walkthroughs macOS-focused. | 04, 23 |
| Get Started | Briefly link to download if needed, then use the default Space without teaching Space setup. Focus on creating and formatting a note, selecting text for the formatting toolbar, and typing `/` to insert elements. Use a small example such as a heading, checklist, and table. End with optional links to AI, Excalidraw, and other features; do not require AI setup. | 05–09 |
| Spaces basics | Add a separate Create and manage Spaces guide covering creating, opening, and switching Spaces. Keep this explanation out of Get Started. | 06, 08 |
| Writing, elements, and tables | Merge Formatting and Command Menu into Writing and formatting. List all released elements in the overview, grouped into everyday and more specialized elements, including HTML and D2. Give Tables its own substantially more detailed guide, covering verified column types and features. | 09–11 |
| Examples | Reuse suitable examples from `/Users/max/Desktop/My Space`, especially Today, for consistent text and screenshot briefs. Read that Space as reference material; this project does not require editing it. | 12 |
| Menu bar | Keep Use Outline from the menu bar visible under Notes. | 13 |
| AI emphasis | Give external AI apps and working with local notes the greater share of the AI section. Treat the requested 30–40% built-in Chat emphasis as editorial balance, not a word-count quota. Distinguish direct file access, Terminal usage, and MCP where their capabilities or setup differ. | 14, 17 |
| AI articles | Write Working with AI now as practical guidance on useful context and reviewing changes. Add Set up AI Chat for Codex/account setup inside Outline; link to it from Start an AI chat. Keep external-app MCP setup in its separate guide. | 15, 24, 25 |
| Resources and Terminal | Use the task-oriented title Add context and reusable content while retaining actual UI labels in the body. Put AI in the Terminal under AI; retain its simple existing approach without installing external command-line tools in the article. | 17, 18 |
| PDF and templates | Add Export a note as a PDF under Notes. Retain and review the existing template usage guide under Notes and template configuration guide under Advanced. | 22, 26 |
| Deferred content | Keep Workflows hidden and retain the drafts. Defer unnamed HTML, Terminal, and Get Started proposals; do not create filler articles. Add no YouTube links or embeds in this revision. | 19, 21 |
| Screenshots | Reuse accurate existing visuals. Where a useful screenshot is missing, leave an explicit placeholder and a precise brief of the UI state to capture. Add the requested screenshots before pushing the documentation. | 15, 20, 27 |

Verify exact UI labels, shortcuts, element support, setup prerequisites, example paths, and asset behavior during implementation. These are evidence checks, not additional editorial questions for the user. If a real product uncertainty remains after checking, record a focused follow-up in the Q&A.

## Agreed top-level structure

The root navigation order will be:

1. Introduction — `intro.md`
2. Get Started — `get-started.md`
3. Notes — `notes/`
4. Spaces — `spaces/`
5. AI — `ai/`
6. Advanced — `advanced/`

Introduction and Get Started are standalone articles. The remaining four items are sections. Advanced stays last. Workflows remains on disk but hidden.

Move files into these four existing folders so the source tree matches the reader-facing structure. Moved or renamed articles change their public URLs; the user accepts retiring the old URLs (answer 03). No redirects are required. Update repository links to their final destinations.

## Article inventory and destination map

All paths in this table are relative to `docs/v0`. “Keep” preserves the article's purpose and path; its accuracy and presentation still need review. “Complete” means the current content is placeholder text, screenshots, or otherwise unfinished. The table accounts for all 32 existing public articles; approved additions follow it.

| Existing article | Action | Final destination | Content decision |
| --- | --- | --- | --- |
| `intro.md` | Complete | `intro.md` | Introduce local notes, macOS/iOS availability, modern note-taking, and agent workflows. Link to Get Started. |
| `get-started.md` | Complete | `get-started.md` | Brief download link, then creating, formatting, and finding a note in the default Space. No Space setup or AI chat in the main journey; end with optional learning links. |
| `notes/formatting.md` | Combine and complete | `notes/writing-and-formatting.md` | Explain everyday writing, formatting, and opening the command menu. |
| `notes/command-menu.md` | Merge into writing guide | `notes/writing-and-formatting.md` | Keep insertion instructions and useful shortcuts; retire the separate source after migration. |
| `notes/elements.md` | Complete | `notes/elements.md` | Briefly describe every released element, grouped into everyday and specialized elements, with links to detailed guides. |
| `elements/table.md` | Move and complete | `notes/tables.md` | A detailed practical guide to creating and using tables, including verified column data types and features. |
| `notes/link-to-notes.md` | Keep | `notes/link-to-notes.md` | Review links, examples, and terminology. |
| `notes/create-a-note-from-a-template.md` | Keep | `notes/create-a-note-from-a-template.md` | Explain using a template; link to Advanced for creating and configuring templates. |
| `excalidraw/create-excalidraw-drawings.md` | Move | `notes/create-excalidraw-drawings.md` | Keep basic drawing creation and editing separate from AI usage. |
| `excalidraw/excalidraw-with-ai-agents.md` | Move | `notes/excalidraw-with-ai-agents.md` | Retain the drawing-focused AI guide and link to general AI/MCP setup. |
| `the-menu-bar.md` | Move and finish | `notes/the-menu-bar.md` | Keep the existing guide visible under Notes as a quick way to create and open notes. |
| `spaces/icloud.md` | Keep | `spaces/icloud.md` | Review storage, Space creation, and cross-Mac instructions. |
| `spaces/choose-where-attachments-are-saved.md` | Keep | `spaces/choose-where-attachments-are-saved.md` | Keep the everyday attachment-folder task. |
| `spaces/hide-files-and-folders-from-the-sidebar.md` | Keep | `spaces/hide-files-and-folders-from-the-sidebar.md` | Keep in-app visibility controls separate from configuration reference. |
| `ai/starting-an-ai-chat.md` | Keep and review | `ai/starting-an-ai-chat.md` | Make it a complete short introduction to Chat, with accurate prerequisites and modes. Add a setup callout linking to Set up AI Chat. |
| `resource-items/use-resource-items.md` | Move and retitle | `ai/add-context-and-reusable-content.md` | Use the title Add context and reusable content. Explain resources using actual UI labels and clarify that they also appear in Terminal. |
| `ai/adding-skills.md` | Keep and review | `ai/adding-skills.md` | Explain using skills; link to Advanced where configuration detail would interrupt the task. |
| `ai/agents-md.md` | Keep | `ai/agents-md.md` | Keep agent guidance with the AI articles. |
| `terminal/ai-in-the-terminal.md` | Move and review | `ai/ai-in-the-terminal.md` | Include the minimum steps for opening a terminal; do not create a separate terminal section for one article. |
| `ai/mcp-server.md` | Keep | `ai/mcp-server.md` | Retain the MCP overview; avoid duplicating full setup and access instructions. |
| `ai/mcp-with-ai-clients.md` | Keep | `ai/mcp-with-ai-clients.md` | Retain external-client setup as a separate task. |
| `ai/manage-mcp-access-for-a-space.md` | Keep | `ai/manage-mcp-access-for-a-space.md` | Retain access management as a separate task. |
| `ai/troubleshoot-outline-mcp.md` | Keep | `ai/troubleshoot-outline-mcp.md` | Keep troubleshooting near MCP setup; link to the tools reference. |
| `advanced/configuration.md` | Keep | `advanced/configuration.md` | Maintain the Space configuration reference; link to specific user-facing guides. |
| `resource-items/configure-resource-items.md` | Move | `advanced/configure-resource-items.md` | Put resource discovery configuration in Advanced. |
| `advanced/add-and-edit-templates.md` | Keep | `advanced/add-and-edit-templates.md` | Retain template setup separately from creating a note from a template. |
| `mcp/view-and-edit-note-frontmatter.md` | Move | `advanced/view-and-edit-note-frontmatter.md` | Place frontmatter with advanced note/Space configuration. |
| `mcp/tools-reference.md` | Move | `advanced/mcp-tools-reference.md` | Keep detailed tool schemas, limitations, and examples out of the beginner flow. |
| `workflows/managing-projects-with-ai.md` | Hide for later | Same path | Preserve the draft without publishing it. |
| `workflows/planning-a-product-launch.md` | Hide for later | Same path | Preserve the draft without publishing it. |
| `workflows/running-weekly-team-meetings.md` | Hide for later | Same path | Preserve the draft without publishing it. |
| `workflows/turning-customer-emails-into-tasks.md` | Hide for later | Same path | Preserve the draft without publishing it. |

Approved additions:

| New article | Destination | Scope and boundaries |
| --- | --- | --- |
| Create and manage Spaces | `spaces/create-and-manage-spaces.md` | Explain what a Space is and how to create, open, and switch Spaces on macOS. Link to storage and iCloud details instead of duplicating them. |
| Working with AI | `ai/working-with-ai.md` | Introduce practical ways to work with local notes using external AI apps and Outline Chat. Explain useful context, note/folder/table/row references where supported, and reviewing changes. Link to the context guide and setup articles for detailed procedures. |
| Set up AI Chat | `ai/set-up-ai-chat.md` | A short first-time guide to enabling the supported Codex connection and connecting an account inside Outline. Include useful screenshot briefs. Keep external-app MCP connection instructions in their existing guide. |
| Export a note as a PDF | `notes/export-a-note-as-a-pdf.md` | Explain single-note export, preview, and saving. Briefly describe relevant page-layout and rich-content limitations after verifying current behavior. |

After the one two-article merge and four additions, the expected public inventory is 35 articles: 31 intended to be visible and four Workflows drafts retained but hidden. Temporarily hidden unfinished articles are additional to those four until completed.

Tracker-only entries need explicit dispositions too:

- **Working with AI:** keep its existing tracker entry Pending until writing starts, then In Progress. Retain the internal research note and create the approved public guide; do not put it On Hold.
- **New Spaces, AI setup, and PDF guides:** add Pending rows with the approved scopes. Add Page links when files are created, then update statuses as writing and review progress.
- **Launch a terminal session:** cover the essential steps in AI in the Terminal; archive the standalone article proposal with a note pointing to the replacement.
- **Formatting and Command Menu:** retain historical tracker rows and mark them Archived only after the combined guide is complete. Add or repurpose a tracker row for Writing and formatting.
- **Blank HTML, Terminal, and Get Started proposals:** the user confirmed none is required for this release. Leave them clearly deferred; archive only proposals that are demonstrably redundant. Keep useful internal material.
- **Workflows:** use On Hold while hidden; keep Scope Public because these are intended future public articles. Internal research and planning remain Scope Internal.

## Final navigation ordering

Set explicit `order` arrays to define the intended sequence. Unlisted children can still appear through fallback sorting, so audit every remaining child and use `hidden` where needed. Each entry must name an existing direct child without `.md` or a path. Update `labels` to match approved article titles.

| Metadata file | Final ordered children |
| --- | --- |
| `docs/v0/meta.json` | `intro`, `get-started`, `notes`, `spaces`, `ai`, `advanced` |
| `docs/v0/notes/meta.json` | `writing-and-formatting`, `elements`, `tables`, `link-to-notes`, `create-a-note-from-a-template`, `export-a-note-as-a-pdf`, `create-excalidraw-drawings`, `excalidraw-with-ai-agents`, `the-menu-bar` |
| `docs/v0/spaces/meta.json` | `create-and-manage-spaces`, `icloud`, `choose-where-attachments-are-saved`, `hide-files-and-folders-from-the-sidebar` |
| `docs/v0/ai/meta.json` | `working-with-ai`, `mcp-server`, `mcp-with-ai-clients`, `manage-mcp-access-for-a-space`, `troubleshoot-outline-mcp`, `ai-in-the-terminal`, `set-up-ai-chat`, `starting-an-ai-chat`, `add-context-and-reusable-content`, `adding-skills`, `agents-md` |
| `docs/v0/advanced/meta.json` | `configuration`, `configure-resource-items`, `add-and-edit-templates`, `view-and-edit-note-frontmatter`, `mcp-tools-reference` |

The AI order starts with general guidance and external-client workflows, then introduces built-in Chat setup and use. Context, skills, and agent guidance support both paths. This ordering implements the requested editorial emphasis without duplicating setup instructions.

An `order` list does not hide omitted children. Add `workflows` to the root `hidden` list and retain `internal`. During implementation, temporarily hide any unfinished visible article in its own directory's metadata until it meets the completion criteria. Add new navigation entries when their files exist; keep new drafts hidden until reviewed. Do not link public articles to hidden pages.

After all moves, remove obsolete labels/order entries and the empty `elements`, `excalidraw`, `resource-items`, `terminal`, and `mcp` directories and their metadata. Do not hide an old copy as a substitute for a redirect: hidden articles also lose direct rendering, search, and sitemap inclusion.

## Part 1 — Consolidate decisions and verify product details

**Objective:** Use the answered Q&A as the editorial baseline and verify the product details needed to write accurate articles.

**Files:** This plan; `/Users/max/Code/outline-docs/docs/v0/internal/Temp/New Doc Structure QA.md`; `/Users/max/Code/outline-docs/docs/v0/internal/Temp/doc-restructure-evidence.md`; `/Users/max/Code/outline-docs/docs/v0/internal/Articles.md`. Read the current Outline product/code when needed for evidence.

**Steps:**

1. Treat answers 01–27 and the decisions above as settled. Preserve the Q&A answers and managed table IDs/configuration. Do not reopen decisions already answered.
2. Keep screenshot placeholders and precise briefs in working article files as needed. Add the screenshots before push; do not publish placeholders.
3. Verify exact UI labels, prerequisites, supported features, shortcuts, and example values against the intended released product. Record concise evidence in internal planning/tracker notes. Keep user decisions, verified facts, and unresolved behavior distinct; do not invent Q&A answers.
4. Inspect the demo Space and choose consistent examples, including Today where suitable. Confirm the actual default-Space first-use flow without adding Space management to Get Started.
5. Review the linked PDF/template feature summaries and existing template articles. Verify PDF export behavior and built-in Chat setup before drafting the new guides. Verify each external app's currently supported connection path before presenting it as supported; use ChatGPT as an example only where that path is confirmed.
6. Verify the existing root `attachmentsDir` contract: repository guidance lists four metadata fields, while the current local docs application supports this existing version-root asset setting. Preserve working asset resolution and the existing setting unless evidence supports a necessary change; do not silently drop it while rewriting navigation.
7. Add no YouTube links, players, or native-block renderer work. Video is deferred and is not an implementation dependency.
8. Reconcile the approved article additions, scopes, and statuses in the tracker. Keep unwritten articles Pending and retain useful research notes. Do not perform public-content changes during this plan update.

**Deliverable:** This updated plan, aligned task status, and internal product evidence for article preparation.

**Validation/checkpoint:** Editorial decisions affecting drafting are settled, including question 27. Product evidence is recorded in `docs/v0/internal/Temp/doc-restructure-evidence.md`. This preparation checkpoint passed; see the later implementation and validation results. Keep the documentation unpushed until screenshots and released-app checks are complete.

**Dependencies/risks:** The shipped product may differ from older articles or current local development code. Use evidence for the intended release; do not treat tracker statuses as proof of accuracy.

## Part 2 — Move content and configure navigation

**Objective:** Establish the agreed file structure and reader-facing ordering without exposing drafts.

**Files:** The paths in the destination map, all affected `meta.json` files, the article tracker, and links elsewhere in the repository pointing to moved notes.

**Steps:**

1. Recheck repository instructions and working-tree changes. Keep the restructuring unpublished until validation is complete; use the repository's normal review workflow. Preserve unrelated edits.
2. Apply the approved file moves. Preserve article frontmatter, managed IDs, and assets. For Formatting/Command Menu, retain all useful source material until the combined article is written and reviewed in Part 3.
3. Apply the root and section ordering and labels. Keep `internal` hidden, hide `workflows`, and explicitly hide unfinished pages at their current paths. Preserve unrelated metadata consistent with the contract settled in Q&A.
4. Remove metadata references to files that no longer exist. Remove old folders only after their useful contents have been accounted for.
5. Update public links, tracker Page links, and internal note links in the same batch as each move. Check wiki links, root-relative `/docs/v0/...` links, full docs URLs, `.md` destinations, and heading fragments. Preserve private links as internal-only references.
6. Record the before/after public URLs in this internal plan or a linked internal migration note. Old URLs may retire, so no redirect implementation or compatibility dependency is required. Update all repository references to the moved or merged sources.
7. Update article Areas to Notes, Spaces, AI, or Advanced where appropriate. Preserve statuses for moved articles; movement alone does not complete an editorial review.

**Deliverable:** The new folder structure, coherent navigation metadata, updated references, and a recorded URL mapping.

**Validation/checkpoint:** JSON parses; navigation entries reference direct existing children without duplicates or traversal; only the two opening articles and four sections are intended for final visibility. Workflows and internal notes are hidden, unfinished pages stay hidden, moved links resolve locally, and asset destinations remain valid. Review this part before continuing.

**Part 2 implementation checkpoint (2026-10-23):** The ten approved file moves, section metadata, and repository link migration are applied. The before/after routes and staging caveats are recorded in [[docs/v0/internal/Temp/doc-url-migration]]. The existing `attachmentsDir: "Attachments"` setting and all moved managed image references remain intact. `notes/command-menu.md` is retained hidden for the Part 3 merger. New guide slots are intentionally absent from `order` and `labels` until their files exist. Local checks found valid JSON/direct-child references, resolving public web routes and image assets, and a parsed Articles managed table with no diagnostics. Part 3/4 article review and final rendered validation remain pending.

**Dependencies/risks:** Missing `order` entries do not hide pages. Invalid metadata can cause fallback behavior. Old external links may stop resolving under the accepted URL policy; repository links must be updated. Removing a source too soon can lose useful draft material.

## Part 3 — Complete Introduction, Get Started, and Notes

**Objective:** Give a new user a complete path into Outline and finish the core note-writing guides.

**Files:** `docs/v0/intro.md`, `docs/v0/get-started.md`, `docs/v0/notes/*.md`, `docs/v0/notes/meta.json`, article assets, and `docs/v0/internal/Articles.md`.

**Steps:**

1. Write Introduction and Get Started first. Introduction explains local notes and agent workflows and briefly mentions iOS. Get Started gives a macOS download link and a small create/write/format/find journey using the default Space. Show text selection, `/`, and a few elements; end with optional next-step links. Do not teach Space setup or require AI chat.
2. Create Writing and formatting by combining the two source articles. Lead with editing and insertion through the toolbar and command menu; explain useful Markdown terms and shortcuts without making prior Markdown knowledge necessary. After content and links are migrated, remove redundant sources and archive their tracker entries.
3. Complete Elements as a concise overview of all released elements, grouping common elements first and specialized elements such as HTML and D2 afterward. Complete Tables as a separate detailed guide with practical steps and verified column-type/feature coverage. Link from the overview instead of duplicating the table guide.
4. Add Export a note as a PDF, covering the verified menu action, preview, saving, and relevant limitations. Retain the template usage article and link to its existing Advanced setup guide. Review note links, both Excalidraw guides, and the menu-bar guide for accuracy; keep the menu-bar article visible under Notes.
5. Use consistent examples from the demo Space. Inspect every visual in any substantially edited or reviewed article. Reuse accurate screenshots, flag outdated ones, and keep labels and example values consistent. Where a screenshot adds useful clarity but is unavailable, add an explicit `[SCREENSHOT PLACEHOLDER — Screenshot should show …]` callout or code block with the platform, UI state, important elements, and crop guidance. If using a managed image placeholder, preserve the established image-block format with a unique ID and caption brief. Record outstanding screenshots in the tracker and add them before push.
6. Use short introductions followed by `##` sections; do not repeat article titles as body-level `#` headings. Preserve supported frontmatter and use approved navigation labels for display titles.
7. Review and verify each article independently, update its tracker row, and remove its temporary hidden entry only when complete.

**Deliverable:** Reviewed opening articles and Notes drafts, including PDF export, with consistent examples, links, and explicit briefs for missing screenshots.

**Part 3 implementation checkpoint (2026-10-23):** Introduction, Get Started, Writing and formatting, Elements, Tables, and Export a note as a PDF are drafted. Formatting and Command Menu were merged with both existing image blocks retained; the redundant Command Menu file is removed and historical tracker rows archived. Existing Notes articles were reviewed and the local root/Notes navigation now exposes the drafted pages for full review. Get Started needs a current note-creation screenshot and the PDF guide needs an export-dialog screenshot before push; both tracker rows remain In Progress. Source-backed UI details and assets have been checked, but a released-app rendered review and final screenshot replacement remain Part 5 work. No push is authorized.

**Validation/checkpoint:** The text explains the first-use journey without relying on a missing screenshot or hidden page. Every retained Notes article helps complete a clear task. Merged content is preserved, links/assets work, and remaining screenshot work is explicit in the tracker. Keep articles requiring image work In Progress rather than declaring them publication-ready. Review this part before continuing.

**Dependencies/risks:** UI details and table features depend on Q&A evidence. Screenshots may need replacement; keep useful placeholders explicit and track any remaining image work before final publication review.

## Part 4 — Review Spaces, AI, and Advanced

**Objective:** Make the remaining visible articles accurate and complete without adding unnecessary scope.

**Files:** `docs/v0/spaces/`, `docs/v0/ai/`, `docs/v0/advanced/`, their metadata, article assets, and the article tracker.

**Steps:**

1. Write Create and manage Spaces as the first Spaces article, covering creating, opening, and switching Spaces on macOS. Review the existing iCloud, attachments, and visibility articles; link between them without duplicating setup instructions or adding Space management to Get Started.
2. Write Working with AI now, using the retained research as input. Give external apps the greater editorial emphasis and explain the different access paths accurately. Cover useful context and reviewing changes; link to Add context and reusable content for detailed resource/reference procedures. Retain AI in the Terminal under AI, with minimum Terminal-opening steps and no external-tool installation walkthrough.
3. Keep the MCP overview, external-client setup, access management, and troubleshooting as separate articles, before the built-in Chat guides in navigation. Trim repeated explanations and verify client-specific setup rather than implying all external apps use the same integration.
4. Write Set up AI Chat as a short Codex/account setup guide for Chat inside Outline. Review Start an AI chat and add a prerequisite callout linking to setup. Keep supported modes and UI labels accurate. Retitle/move Add context and reusable content, then review skills and agent guidance. Keep built-in Chat around 30–40% of the overall AI emphasis, without forcing an exact length ratio.
5. Review Advanced for correct configuration examples, template setup, frontmatter instructions, and MCP tool details. Retain Add and edit templates as the configuration companion to the usage guide. Keep specialist mechanics out of introductory articles and cross-link usage/setup where helpful.
6. Inspect referenced visuals and verify steps/examples against the Q&A and intended released product. Reuse accurate screenshots or add precise placeholders as described in Part 3. Record any newly discovered product uncertainty internally and add a focused Q&A follow-up only if verification cannot resolve it.
7. Keep the four Workflows drafts hidden and unnamed HTML, Terminal, and Get Started proposals deferred. Working with AI is in scope and must be written. Add no YouTube links or embeds.
8. Update tracker rows and reveal temporarily hidden articles only after their individual content reviews pass. Track unresolved screenshots and publication readiness separately.

**Deliverable:** Reviewed Spaces, AI, and Advanced sections, including the new Spaces, Working with AI, and AI setup guides, with useful boundaries, cross-links, and tracked screenshot work.

**Validation/checkpoint:** Each article's text is useful and accurate, technical examples contain no credentials, and intended public cross-links resolve to reviewed content. Completed statuses require resolved article work; drafts with outstanding screenshots stay In Progress. Check the external-app emphasis and the separate built-in setup/use flow. Review this part before continuing.

**Dependencies/risks:** MCP runtime versions, external-client setup, and settings can change. Verify relevant facts for the release; do not copy older claims without checking them.

**Part 4 implementation checkpoint (2026-10-23):** Spaces, AI, and Advanced were reviewed. Create and manage Spaces, Working with AI, and Set up AI Chat were drafted; AI navigation now places external-client guidance before built-in Chat. Start an AI chat links to setup. Existing iCloud and Skills articles were shortened around their user tasks. Source-backed label and client-path evidence is in `docs/v0/internal/Temp/doc-restructure-evidence.md`. The new Space and AI setup screenshot briefs remain in working article files, with those tracker rows In Progress. The release/rendered review and screenshot replacement remain Part 5 work. No push is authorized.

## Part 5 — Validate the complete documentation and prepare publication

**Objective:** Confirm the final structure is ready to publish as one coherent content change.

**Files/systems:** Changed repository content and metadata; the existing docs application for preview and validation when available. Use its existing tooling without adding tooling or dependencies to this repository.

**Steps:**

1. Compare the final file list with the inventory. Account for every retained, moved, merged, hidden, or removed article; confirm no unfinished public page was missed by fallback navigation.
2. Parse and validate all changed metadata/frontmatter against the current supported contract, including the asset-contract verification from Part 1. Confirm public titles, section ordering, direct-child references, and hidden paths.
3. Check all changed links and incoming references to retired paths, including fragments. Confirm public articles contain no internal tracker, draft, private recording, or planning links. Check local asset existence and rendered image resolution.
4. Use the existing docs preview or application validation workflow to inspect the sidebar, macOS opening journey, representative moved articles, new guides, formatting, tables, and screenshots. No new YouTube links or embeds are in scope. If no rendered preview is available, report that limitation and leave visual validation pending rather than claiming it passed.
5. Verify hidden `internal` and `workflows` content is absent from navigation, search, sitemap, and direct article rendering in the available application environment. Check the default version entry reaches Introduction and Advanced is last.
6. Verify the accepted URL migration: new routes resolve, repository references use their final destinations, and no hidden/retired source remains a public cross-link target. Old public URLs may retire; no redirects are required.
7. Apply answer 27: add every required screenshot before push, replace working placeholders and briefs in public articles, and verify image rendering. Do not expose editorial instructions as finished public content.
8. Reconcile tracker Titles, Areas, Pages, Notes, Scope, and Status. Record replacements on Archived rows and deferred Workflows as On Hold. Account for all four new articles, retain useful internal research/recordings, and confirm any remaining image work is reflected in statuses and notes.
9. Review the complete diff for unintended app/configuration changes, secrets, lost frontmatter, duplicate content, unsupported metadata, and changes to `docs/v1`.
10. Prepare a concise review summary covering structure, content completed, merges/removals, hidden drafts, changed URLs, validation, screenshots, and any remaining limitations. Use the existing repository publication/review process; this plan does not authorize merging or deploying now.

**Deliverable:** A reviewable content change with validation results and a complete migration summary.

**Final checkpoint:** The public documentation contains Introduction, Get Started, and the four agreed sections in order, with all four approved new articles accounted for. Every visible article is complete, accurate, and linked correctly. Optional drafts and internal notes stay hidden. Required screenshots and visual validation are complete before push.

**Part 5 local validation checkpoint (2026-10-23):** All 31 visible articles were parsed and rendered using the current docs application modules. Metadata validation produced no warnings; rendered local links and image paths resolve. The actual docs service, supplied with local files, rejects hidden articles and excludes their Markdown from search. Sampled retired routes return not-found. A browser content preview checked the opening journey, sidebar ordering, Tables images, and AI setup. Managed tables and scope/diff checks pass, and independent content/cleanup review found no further corrections. Details and limitations are in [[docs/v0/internal/Temp/doc-restructure-validation]]. The four screenshot sets and manual released-app/final-site review remain publication work; the overall task stays In Progress.

**Dependencies/risks:** The live site reads published content through caching/webhooks, so local verification alone does not prove the deployed result. After publication is authorized and completed, check representative live routes and visibility once the content refreshes.

## Next action

Add the four screenshot sets listed in [[docs/v0/internal/Temp/doc-restructure-validation]], replace the working briefs, and verify the steps in the intended released macOS app. Review the finished article rendering before arranging publication. Keep this work unpushed until those checks are complete; the local content changes are ready for that review.
