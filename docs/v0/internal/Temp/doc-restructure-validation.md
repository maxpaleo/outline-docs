This is the historical first-restructure checkpoint. The later approved article review is recorded in [[docs/v0/internal/Temp/doc-content-review-validation]], which contains the current inventory and screenshot checklist.

The content restructure is implemented locally and has passed the checks below. The work has not been committed, pushed, merged, or deployed. Publication remains pending the screenshot captures and released-app review described here.

## Content and navigation

- All 32 original public articles are accounted for through the approved moves, the Formatting/Command Menu merge, or retained Workflows drafts. Four new guides bring the final public inventory to 35 files: 31 intended visible articles and four hidden Workflows drafts.
- Root ordering is Introduction, Get Started, Notes, Spaces, AI, Advanced. The version's first visible article is Introduction.
- Directory metadata parses with the actual docs application schemas, has no warnings, and references existing direct children. The existing root `attachmentsDir: "Attachments"` setting is preserved.
- Public article bodies contain no repeated title-level H1, unresolved `[[docs/v0/...]]` references, internal planning links, or links to hidden/retired articles.
- All rendered local article links and heading fragments resolve. Fourteen distinct referenced image assets exist. Existing screenshot assets were inspected; the superseded Get Started welcome-image block is retained in the internal evidence note.

## Application-backed local checks

The temporary validation scripts live outside this content repository. They load the existing docs application's `createDocsNavigation`, `parseDocsDirectoryMetadata`, `parseDocsArticle`, `createDocsService`, and shared Markdown renderer directly. GitHub reads are replaced with local file reads; no real token, remote content write, or application source change is involved.

1. Parsed and rendered all 31 visible articles through the current application pipeline. No metadata warnings, managed-element errors, or broken rendered local links were found. All four screenshot-brief blocks remain identifiable in their working articles.
2. Built the navigation and search projection from the working content. Hidden internal and Workflows articles are rejected by the actual service's article resolver and their Markdown is never fetched for search. The 31 visible articles are searchable. The sitemap source also filters the same `isHidden` property; its deployed endpoint was not exercised.
3. Checked sampled retired routes, including Formatting, Command Menu, Tables, Excalidraw, resource items, Terminal, and the MCP tools reference. They return not-found under the accepted no-redirect policy; replacement routes are present.
4. Inspected Introduction, Get Started, Tables, and Set up AI Chat in a localhost content preview. Followed article links, confirmed the intended sidebar ordering and single titles, and checked table-image rendering. This preview uses the application's parser/navigation/Markdown renderer inside a temporary review shell; it is not the full Next.js website shell or a deployed-site test.
5. Validated edited managed tables and preserved their schemas, column IDs, frontmatter, and unrelated rows. Checked the file inventory against the initial snapshot: `docs/v1`, existing image files, application code, dependencies, and unrelated repository files are unchanged. `git diff --check` passes.
6. Completed an independent content and cleanup review with no actionable article corrections. See [[docs/v0/internal/Temp/doc-restructure-review]].

## Required captures before push

| Working article | Screenshot brief |
| --- | --- |
| [[docs/v0/get-started]] | A newly created Today note, selected in the macOS sidebar, with its title and a few lines of text visible. |
| [[docs/v0/notes/export-a-note-as-a-pdf]] | The loaded PDF export preview with A4 portrait and the Export action. |
| [[docs/v0/spaces/create-and-manage-spaces]] | The New space dialog with Create new and the iCloud/This Mac location choices. |
| [[docs/v0/ai/set-up-ai-chat]] | The Codex first-install Set up Codex state and signed-out sign-in choices. Include installed-but-disabled enablement only if useful. |

Replace each article's working placeholder with the final screenshot and inspect the result. Keep these four article rows and the overall task In Progress until the remaining work is resolved. Do not push the placeholders.

## Verification limits and next step

Product instructions were checked against the current local source and client setup against official documentation, as recorded in [[docs/v0/internal/Temp/doc-restructure-evidence]]. A manual walkthrough in the intended released macOS build and final screenshot inspection remain before publication. The live site's cache refresh, production routing, and full Next.js shell have not been tested with these unpushed files. No application build or broad application test suite was run because this change contains only documentation and navigation data.

Add the screenshots, walk through the new note, Space, PDF, and AI setup instructions in the released app, and review the finished article rendering before arranging publication. The accepted URL changes and mapping are recorded in [[docs/v0/internal/Temp/doc-url-migration]].
