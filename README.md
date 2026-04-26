# Hugo Knowledge Graph Examples

This repository contains example sites for [Hugo Knowledge Graph](https://github.com/ZhenShuo2021/hugo-knowledge-graph), providing three content sources of different scales and types to preview how the knowledge graph renders with real content.

## Quick Start

```sh
git clone https://github.com/ZhenShuo2021/hugo-kg-example
cd hugo-kg-example
hugo server -e NAME
```

Replace `NAME` with one of the following environment names:

| Name | Source | Description |
|------|--------|-------------|
| `docker` | [Docker Docs](https://github.com/docker/docs) | Large-scale technical documentation with a high node count |
| `blog` | [blog.maximeheckel.com](https://github.com/MaximeHeckel/blog.maximeheckel.com/) | Personal blog with a natural link structure |
| `yore` | [Hugo theme Yore docs](https://github.com/ZhenShuo2021/hugo-yore) | Small-scale documentation example |

## Try with Your Site

Move the `content` directory from your site to this repo and run `hugo sever`.

## License

This project is licensed under the MIT License.

Content sources and their respective licenses:

- **blog.maximeheckel.com**: Licensed under CC-BY-NC 4.0. Only the frontmatter and link formats have been modified; all article content remains unchanged.
- **Docker Docs**: Licensed under Apache 2.0. All shortcodes have been removed.

All images/shortcodes are removed.
