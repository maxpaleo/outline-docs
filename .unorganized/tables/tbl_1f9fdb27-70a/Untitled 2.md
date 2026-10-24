---
created: 2026-10-23T15:35:56.118Z
updated: 2026-10-23T15:35:56.118Z
---

Add a development-only content source to the Outline documentation app so the real site can preview the local documentation working copy before anything is committed or pushed. Today, development bypasses the GitHub cache but still reads the registered GitHub branch. The intended result is the same articles, navigation, search, and images rendered from saved local files, including newly created and uncommitted files.

**Status: Implemented and verified.** The normal Turbopack production build hit an environment restriction; the webpack production build and runtime checks passed. This note covers application changes in `/Users/max/Code/outline/apps/outline-docs`. The documentation restructuring and its screenshot requirements remain separate work.

## Agreed behavior

Add one optional, server-only variable in the docs application's local environment:

```dotenv
DOCS_LOCAL_REPOSITORY_PATH=/Users/max/Code/outline-docs
```

- In development, a nonblank value selects the local working copy. A blank or absent value preserves GitHub loading.
- The path names the repository root, not `docs/v0`. Existing version definitions resolve `docs/v0` and `docs/v1`, and version-root metadata still controls the attachment directory, including the existing root `Attachments` folder.
- Read files from disk without using Git's index, a commit, or the current branch. Include saved untracked files and observe edits, renames, and deletions on the next full browser refresh.
- Serve local attachment images as well as local article text. Do not quietly mix local articles with GitHub copies of their attachment images.
- Preserve the current parser, presentation, version routing, metadata validation, hidden-content rules, heading anchors, and search behavior.
- A configured but invalid local location produces a useful error. Do not silently fall back to GitHub.
- Production always uses GitHub, even if the local variable was accidentally inherited. The local asset endpoint returns 404 outside development or when local mode is inactive.
- Local mode does not require GitHub repository credentials. Existing public-site URL configuration and defaults retain their current behavior. GitHub mode retains its existing credential requirements.
- Changing the source variable requires restarting the development server. Editing content or images requires only saving and refreshing the browser.
- Automatic refresh on save, file watchers, a source-switching UI, and preview deployments are outside this change.

## Architecture and scope

Follow `/Users/max/Code/outline/AGENTS.md`, `/Users/max/Code/outline/apps/outline-docs/AGENTS.md`, and `/Users/max/Code/outline/.agents/skills/codebase/architecture-design.md` during implementation. Update the app's GitHub-only guidance where this approved local exception changes the contract.

Keep routes and UI dependent on the existing docs service. Introduce only a small typed content-source boundary with the two operations already used by that service: loading a tree and reading a text file. Make both operations version-aware: pass the validated version and its resolved repository-relative content root, with the registered ref available for GitHub requests. Both registered versions currently use `main`, so a ref alone cannot identify the local directory to read. Adapt the existing GitHub client at this boundary and have the local implementation scan only the requested version root. Keep navigation normalization, article parsing, visibility, and search projection in their existing modules; provider implementations supply content rather than duplicating those rules.

Select the provider once when creating the service from validated server configuration. Keep source selection and filesystem imports out of UI modules. Use a discriminated configuration shape so local mode cannot accidentally require a token and GitHub mode cannot omit one. Preserve the existing exported service methods and GitHub test-injection behavior where practical.

Give the Markdown normalizer a small attachment URL resolver supplied by the service; local normalization must not require GitHub repository settings. Share version-root attachment-directory resolution between navigation and asset loading. An image request should read only the relevant root metadata and image, without enumerating navigation or parsing article bodies.

**Trade-off:** A small filesystem provider reuses the real application's pipeline and is simpler to maintain than a separate preview app or mocking GitHub HTTP inside the running app. A generic plugin registry, new shared package, or second renderer would add unnecessary structure. Use the provider boundary only for the two actual sources.

All implementation belongs to the application repository. Do not add application code, environment files, dependencies, generated content, or a preview server to `/Users/max/Code/outline-docs`. Do not change the template-docs app or shared packages for this feature. No new dependencies should be necessary.

## Current implementation references

Paths below are relative to `/Users/max/Code/outline/apps/outline-docs` unless stated otherwise.

| Module | Current responsibility and planned relevance |
| --- | --- |
| `constants/docs-versions.ts` | Registers `v0` and `v1`, both on `main`, with their content directories. Preserve these definitions. |
| `lib/docs/docs-config.ts` | Validates server settings and currently requires GitHub credentials for content. Add development-only source selection here. |
| `lib/docs/docs-service.ts` | Instantiates the GitHub client and coordinates navigation, articles, and search. Select the content provider here. |
| `lib/docs/github-docs-client.ts` | Owns GitHub transport and fetch policy. Preserve its behavior. |
| `lib/docs/docs-content-root.ts` | Combines the optional repository prefix and version directory. Reuse the same path semantics for local content. |
| `lib/docs/docs-types.ts` | Defines the normalized tree and navigation shapes. Reuse these instead of defining a second navigation model. |
| `lib/docs/docs-article.ts` and `lib/docs/legacy-docs-markdown.ts` | Parse articles and rewrite the exact supported legacy links and attachment references. Add source-aware attachment URL generation at this boundary. |
| `lib/docs/docs-search-cache.ts` | Parses content config and bypasses the derived index cache in development. Adapt it to both config variants. |
| `lib/docs/docs-route-data.ts` | Shares navigation and article results within a render request. Preserve request-scoped reuse. |
| `lib/docs/docs-cache.ts` and `next.config.mjs` | Already disable development fetch caching and Server Component HMR caching. Preserve production tags and invalidation. |
| `constants/routes.ts` | Register the local attachment endpoint so developer route tooling knows it exists. |
| `.env.example` and `AGENTS.md` | Document the variable, its precedence, refresh behavior, and the development-only exception. |

New files should remain under the app's existing `lib/docs`, `app/api`, and `tests` directories. Suggested names are `docs-content-source.ts`, `local-docs-client.ts`, and `app/api/docs/[version]/local-assets/[...path]/route.ts`; use adjacent naming conventions rather than introducing another layer.

## Stage 1 — Configuration and local content loading

Complete the stages in order. Checkpoints are implementation reviews and validation steps, not additional user-approval gates.

### Configuration and the content-source boundary

**Objective:** Express local and GitHub loading as explicit server configuration and preserve existing GitHub behavior before adding filesystem reads.

**Relevant files:** `lib/docs/docs-config.ts`, `lib/docs/docs-service.ts`, `lib/docs/github-docs-client.ts`, `lib/docs/docs-content-root.ts`, `lib/docs/docs-search-cache.ts`, the small new content-source contract, and their existing unit tests.

**Implementation steps:**

1. Add parsing for `DOCS_LOCAL_REPOSITORY_PATH`. Treat whitespace-only values as unset. Require an absolute filesystem path when selecting local mode; validate filesystem existence in the local provider when it is used.
2. Resolve source selection using the actual server environment: only `NODE_ENV=development` can select local mode. Ignore the local setting during builds and production runtime; do not validate or access that path in production.
3. Separate common content settings from GitHub-only credentials using a small discriminated union. Preserve `DOCS_CONTENT_ROOT`, the registered version roots, and current site URL handling. Keep webhook and manual invalidation config independently scoped.
4. Define the minimum provider contract around version-aware tree and text-file operations. Supply the validated version, resolved content root, and registered ref as explicit context; do not copy the ref-only GitHub tree signature into the shared contract. The GitHub adapter may retain its existing repository-wide tree fetch, while local reads and enumeration are scoped to the requested version root. Reuse `DocsTree` and avoid inventing commit semantics for local files. If existing tree types require a SHA, provide a deterministic local identity without shelling out to Git; do not use it as a cross-request freshness cache.
5. Adapt service and search config callers to the union. Keep the GitHub client reachable only through the service/provider boundary. Existing injected fetch tests must still exercise the real GitHub client.
6. Keep all source configuration server-only. Never put the local absolute path or credentials into client props, article metadata, search responses, or browser asset URLs.

**Deliverable:** A typed provider/config boundary with unchanged GitHub functionality and a tested development-only local selection rule.

**Validation:** Test absent/blank local settings, valid local selection without a token, invalid relative paths, GitHub credential validation, and production ignoring both valid and invalid local settings. Run relevant existing config, service, content-root, and search-cache unit tests. Preserve separate webhook/revalidation configuration tests.

**Configuration validation:** GitHub behavior still passes its current tests, and source selection cannot activate local reads outside development.

**Risks/compatibility:** `DocsConfig` is currently assumed to be GitHub-shaped in several callers and fixtures. Update those consumers together; avoid dummy credentials or non-null assertions that hide an invalid local configuration.

### Local articles and directory metadata

**Objective:** Load the working copy through the real service while preserving all existing navigation and article rules.

**Relevant files:** New `lib/docs/local-docs-client.ts`, the content-source boundary, `lib/docs/docs-service.ts`, existing content-root/navigation/error helpers, and focused filesystem/service tests.

**Implementation steps:**

1. Use Node filesystem APIs and canonicalize the configured root. Verify it is a readable directory. Do not require a `.git` folder, Git executable, clean worktree, or particular checked-out branch.
2. Enumerate only the requested version's content directory beneath that root using the existing repository-prefix/version-root rules and explicit provider context. Do not enumerate other registered versions as part of this request. Produce repository-relative tree paths for Markdown and `meta.json`, including directory nodes as needed. Do not recursively scan `.git`, caches, or unrelated repository files.
3. Read text only from the allowed content directories. Reuse safe relative-path validation and verify containment after canonicalization. Skip symlinks when enumerating; reject direct symlink reads so local docs cannot escape the configured directories through a linked file or directory.
4. Discover the saved filesystem state on each new request. Include new untracked Markdown, edited metadata, and removed/renamed articles. Do not keep a process-wide directory listing or parsed-article cache.
5. Report a missing/unreadable configured root or requested version directory as a local configuration/content error. A missing unrelated version must not prevent previewing an existing version. A missing article remains a normal 404.
6. Feed the resulting tree and text through the existing navigation, metadata, frontmatter, managed-table, and legacy-link pipeline. Continue checking hidden status before reading an article body for rendering or search.
7. Use the existing `DocsError` conventions for safe messages. Distinguish local filesystem failures from GitHub upstream failures; retain actionable server-side context without returning raw filesystem errors to the browser.

**Deliverable:** Local Markdown and `meta.json` render through the unchanged app-facing service API, with no GitHub requests in local mode.

**Validation:** Use temporary filesystem fixtures, not modifications to the user's notes. Through the service, verify article text, frontmatter, managed-table rendering, metadata ordering/labels, version separation, hidden direct-route 404s, hidden search exclusion, and optional content-root prefixes. In one fixture, add/edit/rename/delete files between calls and confirm the next call observes each change. Cover missing roots and path/symlink containment. Explicitly verify that `v0` loads when `v1` is absent, and that requesting the absent `v1` produces the expected local content error. Assert that GitHub fetch is never called in local mode.

**Stage checkpoint:** Configuration and GitHub regression checks pass; each registered version works independently when present, saved edits are visible on a new request, and hidden articles remain inaccessible. Review the implementation and focused test results before image work.

**Risks/compatibility:** A working copy can change between listing and reading. Handle an article disappearing as not found; do not claim snapshot consistency or add a watcher/snapshot system for this development workflow.

## Stage 2 — Serve local attachment images

**Objective:** Preview existing and newly added attachment images from disk without fetching their published GitHub versions.

**Relevant files:** `lib/docs/docs-article.ts`, `lib/docs/legacy-docs-markdown.ts`, the local filesystem helper, new `app/api/docs/[version]/local-assets/[...path]/route.ts`, `constants/routes.ts`, and focused normalization/route tests.

**Implementation steps:**

1. Supply a small attachment URL resolver from the service to the existing Markdown normalization boundary. The normalizer must not require GitHub settings in local mode. Preserve exactly the currently supported `Attachments/` Markdown image syntax and normal GitHub URL output; do not add arbitrary relative-link rewriting.
2. Build same-origin local asset URLs containing the registered version and a filename relative to that version's configured attachment directory. Represent local filenames internally as decoded path segments and encode each segment exactly once when building the URL. Preserve literal `%` and `#`, spaces, Unicode, and nested directories. Keep the absolute disk path out of the URL. Keep existing GitHub URL generation unchanged, including its current whole-filename encoding behavior; local segment encoding must not silently change production URLs.
3. Share a small helper for version-root `attachmentsDir` validation and defaults between navigation and asset loading. Asset loading reads the requested version's root `meta.json` when present and applies the existing attachment-directory fallback when that file is absent or its `attachmentsDir` field is omitted or invalid. Preserve existing metadata diagnostics and fallback behavior. Do not enumerate the content tree, rebuild navigation, or parse article bodies for image requests. Support the current root-level `Attachments` directory and the default version-specific attachment directory without copying files into `public`.
4. Implement the endpoint in the Node runtime, gated by both development mode and an active local source. Outside that combination return 404 before resolving filesystem paths. Reuse a small service-level asset operation so the route does not implement an independent source selector or import the GitHub client.
5. Read only recognized image files inside the resolved attachment directory. Use a small explicit allowlist matching the screenshot formats needed here, such as PNG, JPEG, GIF, WebP, and AVIF; return the correct image content type and `X-Content-Type-Options: nosniff`. Do not provide arbitrary repository file download access.
6. Verify the framework's catch-all parameter decoding contract and validate the resulting decoded segments once; do not call `decodeURIComponent` again on already-decoded route parameters. Reject traversal/absolute paths/null bytes/backslashes, and apply canonical containment/symlink checks. An asset URL must never expose Markdown, `meta.json`, `.outline`, `.git`, environment files, or a file outside the attachment directory.
7. Send `Cache-Control: no-store` so overwriting a screenshot at the same filename is visible after refresh. Missing or unsupported images return 404 without falling back to GitHub.
8. Keep explicitly external image URLs external. Preserve existing frontmatter image behavior; if an existing supported frontmatter image form resolves to repository attachments, apply the same local resolver there too. Do not expand the accepted image/link syntax as part of this work.

**Deliverable:** The actual docs app renders local attachment screenshots, including new untracked files, without a second asset hosting process.

**Validation:** Test unchanged GitHub normalization, local URLs and route round trips for spaces, Unicode, literal `%`, literal `#`, percent-like names such as `%2F` and `%2e%2e`, and nested filenames; `attachmentsDir` overrides/defaults; byte-correct image responses and replacement freshness, missing files, unsupported files, traversal and symlink attempts, unknown versions, and 404s with local mode off or in production. Verify that asset requests do not enumerate navigation or read article bodies. Inspect a local article containing an existing image and a temporary new screenshot through the browser.

**Stage checkpoint:** Local articles and their repository attachment images both use the working copy, while the endpoint cannot read beyond the permitted image directory. Review the implementation and focused test results before integration checks.

**Risks/compatibility:** Replacing only Markdown reads would leave attachment previews stale. Production attachment URLs and the narrowly supported legacy normalization contract must remain unchanged.

## Stage 3 — Integration, developer instructions, and verification

### Search, refresh behavior, and integration

**Objective:** Confirm that every content consumer uses the selected source and that browser refresh reliably reflects saved local changes.

**Relevant files:** `lib/docs/docs-search-cache.ts`, `lib/docs/docs-route-data.ts`, docs/search routes, sitemap route, existing integration tests, and `next.config.mjs` only if a demonstrated issue requires a change.

**Implementation steps:**

1. Route navigation, article rendering, metadata, sitemap generation, and search-index generation through the same selected service. Do not let one consumer separately parse a GitHub-only configuration or fetch GitHub directly.
2. Preserve React's within-request reuse of route data. Preserve the existing development bypass for content and derived search caches and `serverComponentsHmrCache: false`.
3. Confirm the browser requests a fresh local search index after a full reload. Do not add search polling or background invalidation; the promised refresh action is a full browser refresh, not merely closing/reopening a dialog that may retain its index.
4. Preserve hidden-content exclusion in navigation, direct rendering, search, and sitemap. Preserve `indexable` semantics, heading fragments, and current route handling, including `index.md` articles.
5. Preserve production fetch cache keys/tags, webhook invalidation, manual refresh behavior, and GitHub error handling. Local development should not need a webhook or revalidation request.

**Deliverable:** One consistent local preview across the real site, with production behavior unchanged.

**Validation:** Extend existing route/search tests with a small local fixture. Verify metadata, sidebar, rendered body, heading links, search passages, and sitemap share the expected visible inventory. Edit a fixture's body and navigation and confirm new requests reflect both. Run existing production/GitHub cache and invalidation tests as regression checks.

**Integration validation:** No content consumer bypasses source selection, and refreshing the browser updates local body text, navigation, images, and search.

**Risks/compatibility:** Local files are outside the Next.js app tree, so automatic HMR is not assumed. Browser refresh is the initial supported workflow. Preserve caching in production rather than disabling it globally to achieve local freshness.

### Developer instructions and final verification

**Objective:** Make local preview straightforward to use and verify it against the actual documentation working copy.

**Relevant files:** App `.env.example`, app `AGENTS.md`, the app's existing developer documentation if present, focused tests, and this plan's completion notes. Do not add a public Help Center article for this internal workflow.

**Implementation steps:**

1. Document the optional variable in the app's `.env.example`, using a generic repository-root example and explaining that it is development-only. Explain that GitHub credentials remain required only for GitHub mode.
2. Update app guidance describing GitHub as the sole source to include this explicit development exception, provider boundary, and local asset route. Preserve unrelated guidance and production rules.
3. Document the setup: set `DOCS_LOCAL_REPOSITORY_PATH` in the app's ignored local environment file, start/restart the normal dev command, open `/docs/v0`, save a note in the content repository, and fully refresh the browser. Removing the variable and restarting restores GitHub loading.
4. Document scope: saved disk state is previewed; commits/pushes are unnecessary; no automatic refresh is promised; an invalid path fails visibly; production ignores the variable. Do not log tokens or copy real credentials into documentation.
5. Preserve existing local environment values if configuring the developer's machine is requested during implementation. Do not commit local environment files or silently overwrite them.
6. Run required checks using the already-installed toolchain. Follow `/Users/max/Code/outline/.agents/references/testing.mdc` and the app guide: focused tests, unit tests, integration tests, combined tests, typecheck, lint, and build. Enable Corepack before any pnpm command and use the repository-pinned version; do not reinstall dependencies or update lockfiles.
7. Start the real Next.js app in local mode against `/Users/max/Code/outline-docs`. Inspect representative articles that currently exist; check sidebar order, working images, internal links, and search. Introduction, Get Started, Tables, and Set up AI Chat are optional examples when available. Verify hidden content using fixtures and any currently hidden real articles. Completion must not depend on restructuring documentation, finishing particular articles, or replacing screenshots.
8. Verify edits using temporary fixtures first. If a real working-copy edit is useful for browser verification, use a clearly temporary new test note/image, remove it afterward, and verify cleanup without reverting unrelated user edits.
9. Run the build/production-mode checks with the local variable present and demonstrate that the local provider and asset endpoint remain inactive. Use existing mocked fixtures or configured GitHub access as appropriate; distinguish an external credential/network blocker from a feature failure.
10. Record the actual checks/results and remaining limitations in this note. Do not mark the documentation screenshot work complete or push the content repository as a consequence of this application feature.

**Deliverable:** Implemented local preview, concise developer instructions, regression results, and a manual verification report using the real application.

**Final stage checkpoint:** All acceptance criteria below pass. Review the final diff for unrelated changes, secrets, generated files, and accidental template/shared-package changes before handoff.

**Risks/dependencies:** Implementation requires write access to the separate Outline application repository at `/Users/max/Code/outline`; the current session has that access. Keep application edits there and content-plan edits here. Existing dependencies should suffice. Any unavailable check must be reported accurately rather than treated as passed.

## Acceptance criteria

- With the local variable set in development, `/docs/v0` shows the uncommitted documentation structure from `/Users/max/Code/outline-docs/docs/v0`.
- Existing registered versions and content-root rules work without changing the version registry.
- Saving an article or `meta.json`, creating/deleting/renaming an article, and replacing/adding a screenshot are reflected after full browser refresh.
- Local search contains the current visible working-copy content and uses the same heading destinations as the renderer.
- Hidden content remains excluded from direct article rendering, navigation, search, and sitemap.
- Local content preview works without GitHub credentials and makes no GitHub content requests. Explicit external resources retain their existing behavior.
- Bad local configuration fails clearly; there is no silent switch to published content.
- Local image requests cannot read arbitrary files or escape the configured attachment directory.
- With the variable unset, development still reads GitHub exactly as before. Production reads GitHub regardless of the variable and exposes no local assets.
- No article, image, or local environment file is committed or pushed merely to make preview work. No application code is added to the content repository.

## Completion record

Implemented and reviewed on 2026-10-23. All three stages are complete. Application changes are confined to `/Users/max/Code/outline/apps/outline-docs`; this plan is the only intentional content-repository edit for the feature. The documentation restructuring and screenshot work remain separate.

- **Stage 1:** Added discriminated local/GitHub server configuration, a version-aware tree/text source contract, and a filesystem provider. Local reads include saved untracked files, require no Git state or GitHub credentials, scope enumeration to the requested version, and reject symlink/path escapes. Existing navigation, frontmatter, managed-table, legacy-link, visibility, and search processing remain shared.
- **Stage 2:** Added the development-only local image endpoint and attachment URL resolver. Navigation and asset reads share attachment-directory resolution. Image requests read only version-root metadata and image bytes, allow PNG/JPEG/GIF/WebP/AVIF, reject unsafe paths and symlinks (including case-insensitive `.git`/`.outline` segments), encode decoded filenames exactly once, and return no-store responses. Production GitHub attachment encoding and absolute frontmatter images are unchanged.
- **Stage 3:** Updated `.env.example`, app guidance, and developer instructions. Verified routes, search, sitemap, saved-content freshness, image replacement, and production source isolation. No dependencies, lockfiles, shared packages, template apps, or local environment files were changed. No commit or push was made.

### Automated checks

Commands ran from `/Users/max/Code/outline/apps/outline-docs` using installed binaries. Corepack was enabled and confirmed pnpm **9.15.9** before using pnpm.

| Check | Command | Result |
| --- | --- | --- |
| Initial GitHub/config regression | `./node_modules/.bin/vitest run tests/unit/docs-config.test.ts tests/unit/docs-service.test.ts tests/unit/docs-content-root.test.ts tests/unit/docs-search-cache.test.ts tests/unit/docs-article.test.ts tests/unit/github-docs-client.test.ts` | 6 files, 34 tests passed |
| Focused local/config checks after final path changes | `./node_modules/.bin/vitest run tests/integration/local-docs.test.ts tests/unit/docs-config.test.ts` | 2 files, 26 tests passed |
| Unit | `./node_modules/.bin/vitest run tests/unit` | 33 files, 162 tests passed |
| Integration | `./node_modules/.bin/vitest run tests/integration` | 4 files, 31 tests passed |
| Combined | `./node_modules/.bin/vitest run` | 37 files, 193 tests passed |
| Typecheck | `./node_modules/.bin/tsc --noEmit` | Passed, including after final focused tests |
| Lint | `./node_modules/.bin/eslint .` | Passed with 0 errors and 3 existing warnings: two `E2E_BASE_URL` Turbo declarations in `playwright.config.ts`, and the empty matcher interface in `tests/helpers/vitest-matchers.d.ts` |
| Default production build | `DOCS_LOCAL_REPOSITORY_PATH=/Users/max/Code/outline-docs ./node_modules/.bin/next build` | Initial sandbox attempt could not fetch Google Fonts. Network-enabled retry hit Turbopack CSS-worker internal port binding `EPERM`; environment limitation remains |
| Production build fallback | `DOCS_LOCAL_REPOSITORY_PATH=/Users/max/Code/outline-docs ./node_modules/.bin/next build --webpack` | Passed: compilation, TypeScript, static generation, and route output |
| Diff validation | `git diff --check` | Passed |

Temporary filesystem fixtures cover local selection without credentials, production ignoring valid/invalid local paths, metadata ordering/labels, frontmatter, managed tables, hidden direct/search/sitemap exclusion, heading destinations, prefixes, version independence (v0 works while v1 is absent), add/edit/rename/delete freshness, safe paths and symlinks, image bytes/replacement/defaults, literal `%`, `#`, spaces, Unicode, percent-like filenames and nested images. GitHub is never called in local fixtures. Existing GitHub cache and invalidation regression suites passed.

### Runtime and browser verification

The real dev app ran against `/Users/max/Code/outline-docs` with empty GitHub repository/token values supplied only to the process. Playwright CLI was used because the Browser plugin was unavailable. Desktop checks rendered Introduction, Get Started, Tables, and Set up AI Chat; followed the Introduction → Get Started internal link; confirmed the current sidebar order; and loaded existing Tables screenshots. Screenshot evidence is at `/private/tmp/outline-docs-tables.png`.

A uniquely named temporary untracked article and image directory verified saved new content in the sidebar, rendered body, and search dialog. A new image containing spaces, `#`, literal `%2F`, and Unicode loaded successfully. Real HTTP requests for literal `%2F.png` and `%2e%2e.png` returned 200, confirming Next's already-decoded catch-all parameter contract. Full browser reload reflected changed body text and refreshed search passages; the reopened dialog found the new sentence, and selecting a result landed on the rendered `#preview-heading`. Replacing the image at the same filename returned the updated disk SHA-256. A real hidden `/docs/v0/internal/Articles` request returned 404, and internal/workflows articles were absent from the local search index.

Normal article checks had no relevant runtime errors or framework overlay. The deliberate hidden-route probe produced its expected browser 404 console entry; Next also logged a CSS preload warning and temporary HMR disconnects during the planned server restart. No mobile or additional-browser QA was performed.

The webpack production server ran briefly on `localhost:3012` with an invalid local path and empty GitHub credentials. Local assets returned 404; docs rejected missing GitHub configuration rather than reading that local path. Production/GitHub behavior with valid credentials is covered by existing mocked regression tests; no live authenticated GitHub content fetch was performed. The temporary production server was stopped.

All temporary content and images under `docs/v0/local-preview-qa-20261023.md` and `Attachments/local-preview-qa-20261023/` were removed. The app's `.env.local` was preserved. Next's generated agent-guidance block was removed from the feature diff. Build/dev commands regenerate `next-env.d.ts`: restarting development restored its `.next/dev/types/routes.d.ts` and `.next/dev/types/root-params.d.ts` imports, matching the initial 2-addition/2-deletion generated-file diff size. Its exact original bytes were not captured, so byte-for-byte preservation cannot be independently confirmed; no manual reconstruction was made.

### Ready for local testing

The development server remains running at **http://localhost:3011/docs/v0** (redirects to Introduction). Open that URL, save a note or image in the content working copy, and fully refresh. The active server uses process-scoped local configuration; future server starts can use the documented `DOCS_LOCAL_REPOSITORY_PATH` setup in the app's ignored environment file. Changing or removing that variable requires a restart. No automatic refresh on save is promised.
