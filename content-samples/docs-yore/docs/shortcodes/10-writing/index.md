---
title: Writing
slug: writing
weight: 2000
date: 2026-01-17T10:40:00+08:00
description: "Master Hugo shortcodes for admonitions, figures, lightboxes, lead text, and tabs."
tags: ["shortcodes", "writing", "markdown", "images"]
series: ["Shortcodes"]
---

## Admonition

Admonitions allow you to insert eye-catching callout boxes in your content.

**Example: Markdown syntax with custom icon**

```md
> [!TIP]+ Custom Title
> This is a collapsible tip with a custom icon.
{icon="twitter"}
```

> [!TIP]+ Custom Title
> This is a collapsible tip with a custom icon.
{icon="twitter"}

> [!INFO]- Supported types
> Valid admonition types include [GitHub alert types](https://github.blog/changelog/2023-12-14-new-markdown-extension-alerts-provide-distinctive-styling-for-significant-content/) and [Obsidian callout types](https://help.obsidian.md/callouts). The types are case-insensitive.
>
> **GitHub types:** `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION`
> **Obsidian types:** `note`, `abstract`, `info`, `todo`, `tip`, `success`, `question`, `warning`, `failure`, `danger`, `bug`, `example`, `quote`

## Figure

Other than the markdown image syntax `![](img.jpg)`, Yore includes a `figure` shortcode for adding images to content. It provides more detail control to the markdown syntax.

You should always choose markdown syntax unless you need to insert custom classes to the images.

| Parameter | Description |
| --- | --- |
| `src` | **Required.** The local path/filename or URL of the image. |
| `alt` | Alternative text description for the image. |
| `caption` | Markdown for the image caption, displayed below the image. |
| `class` | Additional CSS classes to apply to the image. |
| `href` | URL that the image should be linked to. |
| `target` | The target attribute for the `href` URL. |

**Example: Image with caption and link**

```md
```

<details>
<summary>Markdown syntax example</summary>

```md
![Alt text](/img/07.webp "A beautiful photo from [Pixabay](https://pixabay.com/images/search/user_id%3a127419%20plane/)")
```

![Alt text](/img/07.webp "A beautiful photo from [Pixabay](https://pixabay.com/images/search/user_id%3a127419%20plane/)")

[Markdown attributes](https://gohugo.io/content-management/markdown-attributes/) is also supported, for example:

```md
![qwe](/img/animated-webp-supported.webp "[Source](https://mathiasbynens.be/demo/animated-webp)")
{class="center-img center-cap"}
```

![qwe](/img/animated-webp-supported.webp "[Source](https://mathiasbynens.be/demo/animated-webp)")
{class="center-img center-cap"}

Note that Markdown attributes require [configuration](https://gohugo.io/content-management/markdown-attributes/) of the Goldmark renderer.

</details>

## Lead

`lead` is used to bring emphasis to the start of an article, typically for introductions or key information.

The input is written in Markdown so you can format it however you please.

**Example: Introductory text**

```md
This is a **bold introduction** to grab the reader's attention.
```

This is a **bold introduction** to grab the reader's attention.

## Tabs

The `tabs` shortcode is used to present different variants of content, such as installation steps or code examples, with optional synchronization.

| Parameter | Description |
| --- | --- |
| `group` | **Optional.** Group name for synchronized tab switching. |
| `default` | **Optional.** Label of the tab to be active by default. |
| `label` | **Required.** The text label displayed on the tab button. |
| `icon` | **Optional.** Icon name to display before the label. |

**Example: Synchronized tabs with icons**

`````md
  ```javascript
  console.log("Hello");
  ```

  ```python
  print("Hello")
  ```

  ```go
  fmt.Println("Hello")
  ```

  ```javascript
  const add = (a, b) => a + b;
  ```

  ```python
  def add(a, b): return a + b
  ```

  ```go
  func add(a, b int) int { return a + b }
  ```
`````

  ```javascript
  console.log("Hello");
  ```

  ```python
  print("Hello")
  ```

  ```go
  fmt.Println("Hello")
  ```

  ```javascript
  const add = (a, b) => a + b;
  ```

  ```python
  def add(a, b): return a + b
  ```

  ```go
  func add(a, b int) int { return a + b }
  ```
