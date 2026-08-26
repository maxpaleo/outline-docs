---
updated: 2026-08-26T22:09:47.519Z
---
# Outline documentation content

This public repository is the content source for [docs.outline-app.co](https://docs.outline-app.co).
It contains versioned Markdown articles and optional directory navigation
metadata. The application in the Outline monorepo fetches this repository from
GitHub; this repository intentionally has no runtime, package manager, build
system, or application code.

## Layout and ownership

Content is kept on the shared `main` branch, with one self-contained directory
per public version:

```text
main
└── docs/
    ├── v0/
    │   ├── index.md
    │   ├── intro.md
    │   ├── ai/
    │   │   ├── meta.json
    │   │   └── ...
    │   ├── attachments/
    │   │   └── ...
    │   └── meta.json
    └── v1/
        ├── index.md
        └── meta.json
```

The application currently maps `v0` and `v1` to `docs/v0` and `docs/v1` on
`main`. A directory alone does not publish a new version: the application
owner must add it to the app's public version registry and deploy that change.

This repository owns Markdown bodies, supported article frontmatter, directory
`meta.json` navigation hints, and version content. The application repository
owns routing, version registration, GitHub access, caching, validation,
rendering, search, webhooks, and deployment configuration.

## Content contract

Only `.md` files become articles. `index.md` is the landing page for its
directory, so `docs/v0/index.md` is served at `/docs/v0`. Use kebab-case for
article and directory names, except for the reserved `index.md` and `meta.json`.

Frontmatter is optional. The supported presentation and SEO fields are:

```yaml
---
title: Install Outline
description: Learn how to get started with Outline.
image: https://example.com/outline-docs.png
indexable: true
keywords:
  - outline
  - documentation
---
```

The supported types are non-empty strings for `title` and `description`, an
absolute URL for `image`, a boolean for `indexable`, and an array of non-empty
strings for `keywords`. Invalid values for supported fields are rejected.
Legacy or source metadata, including fields such as `created` and `updated`,
may remain in migrated Markdown for source fidelity. The web app ignores these
unsupported fields rather than exposing them as presentation or SEO metadata.

An optional directory-local `meta.json` may contain only `label`, `order`,
`labels`, and `hidden`:

```json
{
  "label": "Guides",
  "order": ["getting-started"],
  "labels": {"getting-started": "Start here"},
  "hidden": ["draft"]
}
```

`order`, `labels`, and `hidden` may reference only direct children by their
extensionless name. Names may not contain paths, traversal segments, or the
reserved name `index`; arrays may not contain duplicates. Hidden content is
excluded from navigation, search, sitemap, and direct rendering.

## Contribution workflow

1. Add or edit content beneath the intended `docs/<version>` directory.
2. Keep supported frontmatter values and metadata within the strict contract

  above; preserve legacy/source metadata when migrating existing Markdown.
3. Update the nearest `meta.json` only for direct-child labels, ordering, or

  visibility.
4. Check the route implied by each path and open a pull request against `main`.

After merge, the site receives content through GitHub caching and the
configured push webhook. Content changes do not require an application build.

Never commit tokens, credentials, private keys, `.env` files, or secret-bearing
examples. The application repository owns GitHub and webhook secrets; they
must be configured in deployment settings and never stored here.