---
title: Media and Content Embeddings
slug: media
weight: 2010
date: 2026-01-17T10:40:00+08:00
description: "Explore shortcodes for embedding external media, repository previews, and remote content."
tags: ["shortcodes", "embeddings", "media", "external-content"]
series: ["Shortcodes"]
---

## Article Card

The `article` shortcode generates a visual preview card for a specified internal page.

| Parameter | Description |
| --- | --- |
| `link` | **Required.** The logical path of the target internal page. |
| `showSummary` | **Optional.** Whether the page summary is displayed. **Default:** `true` |
| `lang` | **Optional.** Get page from another language of your site. |

**Example**

```md
```

> [!CAUTION]
> Avoid circular links to prevent infinite recursion.

## Cols

`cols` shortcode allows you to create flexible multi-column layouts with custom widths and optional responsive behaviors. Note that it uses markdown notation (``).

| Parameter | Description |
| --- | --- |
| `widths` | **Optional.** Comma-separated list of column widths (e.g., `30%,70%`). If not specified, columns are evenly distributed. |
| `rwd` | **Optional.** Responsive web design (rwd) controls responsive behavior. When `true`, columns stack vertically on small screens and display horizontally on larger screens. **Default:** `true` |

```md

![qwe](/img/01.webp)

<!-- cell -->

Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit.

```

![qwe](/img/01.webp)

<!-- cell -->

Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit.

See more examples in [rich-content](../../../blog/content-example-2/index.md#cols-shortcode).

## Masonry

`masonry` shortcode allows you to create a fluid, masonry-style image gallery where items are arranged in columns with varying heights. The inner content uses YAML format to define images.

Images can be specified individually with `src`, or batch-loaded with `match`.

| Parameter | Description |
| --- | --- |
| `columns` | **Optional.** The number of columns to display. **Default:** `3` |

**YAML fields per item:**

| Field | Description |
| --- | --- |
| `src` | Image path. Resolves as page resource first, then global resource. |
| `match` | Glob pattern to batch-load images. See [`Match`](https://gohugo.io/functions/resources/match/) for more details. |
| `caption` | **Optional.** Caption text displayed below the image. |
| `alt` | **Optional.** Alt text for accessibility. Falls back to `caption` if omitted. |

**Example**

```yaml

- src: /img/02.webp
  alt: Fly high
  caption: Hello world!
- src: /img/03.webp
  alt: Contrails
- src: /img/04.webp
  alt: Parapet
- src: /img/05.webp
  alt: Wing
- src: /img/06.webp
  alt: Eaves
- src: /img/07.webp
  alt: Biplane sunset
- src: /img/drop.svg
  alt: SVG sample

```

- src: /img/02.webp
  alt: Fly high
  caption: Hello world!
- src: /img/03.webp
  alt: Contrails
- src: /img/04.webp
  alt: Parapet
- src: /img/05.webp
  alt: Wing
- src: /img/06.webp
  alt: Eaves
- src: /img/07.webp
  alt: Biplane sunset
- src: /img/drop.svg
  alt: SVG sample

## Code Importer

The `codeimporter` shortcode fetches source code from a remote URL and renders it as a highlighted code block.

| Parameter | Description |
| --- | --- |
| `url` | **Required.** The absolute URL of the remote source file. |
| `type` | **Optional.** The programming language for syntax highlighting. |
| `startLine` | **Optional.** The starting line number. **Default:** `1` |
| `endLine` | **Optional.** The ending line number. **Default:** `-1` |

**Example: Fetching specific lines from GitHub**

```md
```

## Gallery

The `gallery` shortcode displays an image gallery with a main viewport, navigation buttons, and a scrollable thumbnail strip. The inner content uses YAML format to define images.

Images can be specified individually with `src`, or batch-loaded with `match`.

| Parameter | Description |
| --- | --- |
| `ratio` | **Optional.** Aspect ratio of the slide frame, in `x/y` format. **Default:** `4/3` |
| `fit` | **Optional.** How images fill the frame. `contain` shows the full image (may letterbox); `cover` crops to fill. **Default:** `contain` |
| `thumbs` | **Optional.** Whether to show the thumbnail strip. **Default:** `true` |
| `arrows` | **Optional.** Whether to show the previous/next buttons. **Default:** `true` |
| `counter` | **Optional.** Whether to show the slide counter. **Default:** `true` |

**YAML fields per item:**

| Field | Description |
| --- | --- |
| `src` | Image path. Resolves as page resource first, then global resource. |
| `match` | Glob pattern to batch-load images. See [`Match`](https://gohugo.io/functions/resources/match/) for more details. |
| `caption` | **Optional.** Caption text displayed below the main image. |
| `alt` | **Optional.** Alt text for accessibility. Falls back to `caption` if omitted. |

**Example 1: fit="cover" arrows=false**

```yaml

- match: /img/?[5-7]* # 05, 06, 07
- src: /img/drop.svg
  caption: gallery caption
  alt: gallery alt

```

- match: /img/?[5-7]* # 05, 06, 07
- src: /img/drop.svg
  caption: gallery caption
  alt: gallery alt

**Example 2: thumbs=false counter=false**

```yaml

- match: /img/?[5-7]* # 05, 06, 07
- src: /img/drop.svg
  caption: gallery caption
  alt: gallery alt

```

- match: /img/?[5-7]* # 05, 06, 07
- src: /img/drop.svg
  caption: gallery caption
  alt: gallery alt

## Gist

The `gist` shortcode embeds a GitHub Gist into the page.

| Parameter | Description |
| --- | --- |
| `0` | **Required.** GitHub username. |
| `1` | **Required.** Gist ID. |
| `2` | **Optional.** Specific filename. |

**Example: Embedding a specific file**

```md
```

## GitHub

The `github` shortcode creates a dynamic preview card for a GitHub repository.

| Parameter | Description |
| --- | --- |
| `repo` | **Required.** Format `owner/repo`. |
| `showThumbnail` | **Optional.** Display Open Graph image. **Default:** `true` |

**Example: Repository preview with thumbnail**

```md
```

## Icon

The `icon` shortcode renders an inline SVG icon from the theme's icon library.

| Parameter | Description |
| --- | --- |
| `0` | **Required.** Icon name. |

**Example**

```md
```

See all available icons in [reference page](../../1000-reference-icon/index.md).

## Md Importer

The `mdimporter` shortcode fetches and renders remote Markdown content. With the `md` optional combines with the [markdown notation](../../80-advanced/900-markdown-and-hugo/index.md#hugo-shortcodes), and the imported markdown could render TOC.

| Parameter | Description                                                                   |
| --------- | ----------------------------------------------------------------------------- |
| `url`     | **Optional.** The absolute URL of the Markdown file.                          |
| `page`    | **Optional.** The logical path of the target internal page.                   |
| `md`      | **Optional.** Whether to render the imported the content to markdown.         |

**Example**

General import:

```md
```

Render content TOC:

```md
```

Include an internal page:

```md
```

## Video

The `video` shortcode embeds a HTML5 video player.

| Parameter | Description |
| --- | --- |
| `src` | **Required.** Video URL or local path. Local lookup order: page resource → `assets/` → `static/`. |
| `poster` | **Optional.** Poster image URL or local path. If omitted, the shortcode attempts a same-name image in the page bundle. |
| `caption` | **Optional.** Markdown caption shown below the video. |
| `autoplay` | **Optional.** Enables autoplay when `true`. **Default:** `false` |
| `loop` | **Optional.** Loops when `true`. **Default:** `false` |
| `muted` | **Optional.** Mutes when `true`. **Default:** `false` |
| `controls` | **Optional.** Shows the browser's default playback controls when `true`. **Default:** `true` |
| `playsinline` | **Optional.** Inline playback on mobile when `true`. **Default:** `true` |
| `preload` | **Optional.** `metadata` (load info), `none` (save bandwidth), or `auto` (preload more). **Default:** `metadata` |
| `start` | **Optional.** Start time in seconds. |
| `end` | **Optional.** End time in seconds. |
| `ratio` | **Optional.** Reserved aspect ratio for the player. Supports `16/9`, `4/3`, `1/1`, or custom `W/H`. **Default:** `16/9` |
| `fit` | **Optional.** How the video fits the ratio: `contain` (no crop), `cover` (crop to fill), `fill` (stretch). **Default:** `contain` |

**Example: Autoplay muted video**

```md
```

## YouTube

The `youtubeLite` shortcode embeds an optimized YouTube video player.

| Parameter | Description |
| --- | --- |
| `id` | **Optional.** YouTube video ID. |
| `params` | **Optional.** URL parameters. |

**Example: Specific video with start time**

```md
```

## TypeIt

The `typeit` shortcode creates dynamic typewriter animations.

| Parameter | Description |
| --- | --- |
| `initialString` | **Optional.** Text shown before animation. |
| `speed` | **Optional.** Typing speed in ms. **Default:** `100` |
| `loop` | **Optional.** Whether to restart. **Default:** `false` |
| `tag` | **Optional.** HTML tag for wrapping. **Default:** `div` |

**Example: Looping animation with custom speed**

```md
Yore - A Simple Yet Powerful Hugo Theme
```

Yore - A Simple Yet Powerful Hugo Theme
