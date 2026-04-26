---
title: Page Actions
slug: page-actions
weight: 125
date: 2026-04-19T06:50:00+08:00
description: "Per-page action menu with copy URL, copy Markdown, and view repo source."
tags: ["page-actions", "configuration", "documentation"]
series: ["Documentation"]
series_weight: 125
---

Page actions add a per-page dropdown menu with utilities for sharing and inspecting content.

## Configuration

| Key | Type | Description |
|---|---|---|
| `pageShowActions` | bool | Show the page actions menu, can also be set in front matter |
| `repoURL` | string | Branch root URL, enables *View Repo Source* |
| `repoSubdir` | string | Path from repo root to Hugo project directory |

The `repoURL` must point to the branch root, not the repository root. If the Hugo project lives in a subdirectory of the repository, set `repoSubdir`. Config example:

```yaml {title="hugo.yaml"}
params:
  pageShowActions: true
  repoURL: https://github.com/example/my-site/blob/main
  repoSubdir: exampleSite  # omit if Hugo project is at repo root
```

## Actions

| Action | Condition |
|---|---|
| Copy URL | Always present |
| Copy Markdown | Requires `markdown` in page outputs |
| View Source | Requires `markdown` in page outputs |
| View Repo Source | Requires `repoURL` |

To enable Copy Markdown and View Source, add `markdown` to the page outputs:

```yaml {title="hugo.yaml"}
outputs:
  page:
    - HTML
    - markdown

outputFormats:
  markdown:
    mediaType: text/markdown
    baseName: index
    rel: alternate
    isPlainText: true
    isHTML: false
```
