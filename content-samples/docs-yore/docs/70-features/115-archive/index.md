---
title: "Archive"
slug: "archive"
description: "Enable a comprehensive archive page to aggregate and display all posts across your site."
weight: 115
date: 2026-01-21T08:52:00+08:00
tags: ["archive", "list-page", "configuration", "documentation"]
series: ["Documentation"]
series_weight: 115
---

Yore provides a dedicated archive feature to aggregate all posts into a single chronological list.

## Basic Setup

To enable the archive page, create an `_index.md` and set `listScope: site` in its front matter. Note the file must be named `_index.md`, using `index.md` will prevent Hugo from treating it as a list page.

To exclude a page from the archive, add `pageNoList` to its front matter.

> [!NOTE]
> `pageNoList` also excludes the article from search results but not from the sitemap.
>
> Yore uses Hugo's [built-in sitemap][sitemap-source], you would need to customize it to exclude the page. See [official documentation][sitemap-doc].

[sitemap-source]: https://github.com/gohugoio/hugo/blob/v0.154.5/tpl/tplimpl/embedded/templates/sitemap.xml
[sitemap-doc]: https://gohugo.io/templates/sitemap/
