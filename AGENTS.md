# Outline docs content rules

- This is a public, content-only repository for `https://docs.outline-app.co`.
  Do not add application code, `package.json`, lockfiles, dependencies, build
  output, or environment files.
- Keep each version self-contained beneath `docs/<version>` on `main`. The
  currently registered scaffolds are `docs/v0` and `docs/v1`.
- Use kebab-case for Markdown filenames and directories. `index.md` is the
  landing article for its directory; `meta.json` is directory navigation data.
- Frontmatter may contain only `title`, `description`, `image`, `indexable`, and
  `keywords`, with the types documented in `README.md`.
- `meta.json` may contain only `label`, `order`, `labels`, and `hidden`.
  References must name direct children and must not contain paths or traversal.
- Never commit secrets, tokens, credentials, private keys, `.env` files, or
  secret-bearing command examples. Application and webhook configuration stays
  in the Outline monorepo/deployment settings.
