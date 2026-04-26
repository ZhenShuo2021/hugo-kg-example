---
title: "Docs Layout"
weight: 110
date: 2026-03-18T22:57:00+08:00
description: "Documentation for the 3-column specialized documentation layout."
tags: ["layout", "documentation", "configuration"]
series: ["Documentation"]
series_weight: 110
---

Yore provides a `docs` layout specifically engineered for deep documentation, featuring a 3-column structure to optimize navigation and readability.

## Activation

The `docs` layout can be applied to content using the following methods:

- Directory-based (Automatic)

    Place your Markdown files within the `content/docs/` directory. Hugo will automatically assign the `docs` type to these pages.

- Configuration

    To apply the layout to specific paths or sections without moving files, utilize the `cascade` option in `hugo.yaml`:

    ```yaml
    cascade:
      - type: docs
        target:
          path: '{/shortcodes,/shortcodes/**}'
    ```

    `cascade` can also be configured in the front matter in `shortcodes/_index.md`:

    ```yaml
    ---
    title: Shortcode Section
    cascade:
      type: docs
    ---
    ```

## Options

- Section (_index.md)
  - `params.docsNavCollapsed`: bool, whether the section navigation is collapsed.
- Page (index.md)
  - `params.docsIcon`: string, the icon for the specific entry.
  - `params.docsIconClass`: string, CSS classes applied to the docsIcon wrapper.
- Both
  - `linkTitle`: string, short link title displayed in the navbar.

## Acknowledgement

A large part of Yore's docs layout is built upon the solid foundation of [Docusaurus](https://github.com/facebook/docusaurus).
