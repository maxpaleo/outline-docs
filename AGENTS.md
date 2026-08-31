---
updated: 2026-08-28T18:14:53.064Z
---
# Outline docs content rules

- This is a public, content-only repository for `https://docs.outline-app.co`.
Do not add application code, `package.json`, lockfiles, dependencies, build
output, or environment files.
- Keep each version self-contained beneath `docs/<version>` on `main`. The
currently registered scaffolds are `docs/v0` and `docs/v1`.
- Use kebab-case for Markdown filenames and directories. `index.md` is the
landing article for its directory; `meta.json` is directory navigation data.
- Frontmatter may include the supported presentation and SEO fields `title`,
`description`, `image`, `indexable`, and `keywords`, with the types documented
in `README.md`. Legacy or source metadata such as `created` and `updated` may
remain in migrated notes and is ignored by the web app. Invalid values for
supported fields remain rejected.
- `meta.json` may contain only `label`, `order`, `labels`, and `hidden`.
References must name direct children and must not contain paths or traversal.
- Never commit secrets, tokens, credentials, private keys, `.env` files, or
secret-bearing command examples. Application and webhook configuration stays
in the Outline monorepo/deployment settings.



## Outline-managed agent guidance

Outline keeps this section updated. Put custom instructions outside it. To disable it, turn off “Keep Outline agent guidance up to date” in Space settings.

- This folder is an Outline space. Markdown files are the source of truth for notes.
- `.outline/space.json` is the Space config. Edit it only when asked, preserving existing and unrelated fields plus valid JSON.
- Local assets referenced by notes are stored in the Space-relative directory configured by `attachments.directory` in `.outline/space.json`.
- Preserve note frontmatter and avoid rewriting note content unless requested.
- For ordinary structured data, use GFM tables. For managed Outline tables, first load the `outline-tables` runtime skill; if it is unavailable, read the installed `../../agents/outline-tables.md` reference when accessible; if neither is available and MCP exposes `get_agent_docs`, call it with `{ doc: "outline-tables" }`.
- For richer static visuals, use `html-preview` blocks. First load the `outline-html-preview` runtime skill; if it is unavailable, read the installed `../../agents/html-preview-elements.md` reference when accessible; if neither is available and MCP exposes `get_agent_docs`, call it with `{ doc: "html-preview" }`.
- A note title comes from its filename; do not repeat it as a heading in the note.



# Help Center agent guide

This folder contains Outline's public Help Center and the internal material used to plan and manage it.

## Internal

`Internal` is for the Outline team and must not be treated as public-facing content. It may contain article planning, research, recordings, drafts, and other editorial notes.

`Internal/Articles.md` is the source of truth for tracking Help Center articles. Keep its table updated when planning, creating, moving, or completing an article.

- **Title** identifies the article.
- **Status** tracks whether it is Pending, In Progress, Completed, On Hold, or Archived.
- **Area** groups related articles by product topic.
- **Page** links to the finished article.
- **Notes** is the internal summary field and may link to a separate note containing research, requirements, a draft, or other internal context.
- **Scope** identifies whether an entry is Internal or Public.
- **Video** may link to a supporting recording.

Internal notes may be detailed and technical, but they should not be placed in `Public` unless rewritten for users.

## Public

`Public` contains user-facing Help Center articles. Organize related articles into topic folders and link between them when it helps readers continue a task.

Do not include internal planning, implementation details, private links, or team-only instructions in public articles.

## Writing public articles

Keep articles simple, short, and easy to understand.

- Write for users, not for the team implementing the feature.
- Use plain language and explain unfamiliar terms briefly.
- Lead with what the feature helps the user do.
- Prefer short paragraphs and concrete steps.
- Include only the detail needed to complete the task.
- Put advanced or specialized instructions in a separate linked article when they would make the main article harder to follow.
- Verify that instructions match the current product and that all note links resolve.

### Article titles

Treat the note's filename as the article title.

- Do not repeat the title as a level-one (`#`) heading in the article body.
- Begin the article with its introductory paragraph, then use level-two (`##`) headings for sections.
- Give the file the exact user-facing title the article should display.
- When changing an article's title, rename the file and update links to it instead of adding a separate heading.

## Screenshots and examples

When an article includes screenshots or other visual examples:

- Inspect the visuals and confirm that they match the current product and the article's instructions.
- Keep visible paths, filenames, labels, commands, and example values consistent between the text and screenshots whenever possible.
- If a screenshot is outdated or conflicts with accurate instructions, do not make the text inaccurate just to match it. Notify the developer that the visual should be updated.
- Check every visual referenced by an article when substantially editing or reviewing that article.
- Proactively suggest screenshots when they would make a feature, interface, or workflow easier to understand.
- When the final screenshot is unavailable, you may add a placeholder image at the intended location in the article. Use a unique image block ID.
- Add a concise screenshot brief as the placeholder's caption. Specify the app or platform, the relevant UI state, the important elements to show, and any useful cropping or zoom guidance.
- Add placeholders only when a screenshot provides meaningful clarity. Avoid decorative or repetitive visuals.

### Example:

```
<!-- outline:block id="img_a65a3d80-352" type="image" version="1" assetId="Attachments/placeholder 2.png" src="Attachments/placeholder 2.png" alt="placeholder 2.png" -->
![placeholder 2.png](<Attachments/placeholder 2.png>)

Add a screenshot of the macOS app with the chat open. Frame it tightly around the chat area and composer.
<!-- /outline:block -->
```

