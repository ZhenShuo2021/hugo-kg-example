---
title: "Reference - Configuration"
weight: 994
date: 2026-01-15T14:45:00+08:00
description: "Detailed reference for theme-specific configuration and front matter variables."
tags: ["configuration", "hugo.yaml", "settings", "reference", "documentation"]
series: ["Documentation"]
series_weight: 994
---

The preconfigured `hugo.yaml`.

<!--more-->

<style>
  .lntable {max-height: 75vh; overflow: auto;}
  .highlight-wrapper:not(:has(table)) pre.chroma {max-height: 75vh; overflow: auto;}
</style>

```yaml
# See full options in https://gohugo.io/configuration/all/
# [advanced] = Advanced setting, safe to ignore
theme: hugo-yore
baseURL: https://yore.zsl0621.cc
defaultContentLanguage: en

# pluralizeListTitles: true  # Auto-pluralize list page titles (e.g., "Post" to "Posts")
capitalizeListTitles: false

summaryLength: 30
enableRobotsTXT: true
hasCJKLanguage: false # Enable for Chinese, Japanese, or Korean content to improve word count accuracy. Can be overridden in each language config.
enableEmoji: true

# =============================================================================
# Last modification date
# =============================================================================
# Automatically set the front matter lastmod field to the Git modification date.
enableGitInfo: true
frontmatter:
  lastmod: ['lastmod', ':git', ':fileModTime', ':default']

# =============================================================================
# Pagination
# =============================================================================
pagination:
  pagerSize: 20
  path: 'p'

# =============================================================================
# Taxonomies
# =============================================================================
taxonomies:
  tag: tags
  category: categories
  series: series
  author: authors

# =============================================================================
# Sitemap
# =============================================================================
sitemap:
  changefreq: weekly
  filename: sitemap.xml
  priority: 0.5

# =============================================================================
# Outputs
# =============================================================================
outputs:
  home:
    - HTML
    - RSS
    - fuse-search
    - backlinks
  page:
    - HTML
    - markdown

# [advanced] Required by the theme outputs above, do not modify.
outputFormats:
  fuse-search:
    mediaType: application/json
    baseName: fuse-search
    isPlainText: true
    notAlternative: true
    weight: 10
  backlinks:
    mediaType: application/json
    baseName: backlinks
    isPlainText: true
    notAlternative: true
    weight: 1
  markdown:
    mediaType: text/markdown
    baseName: index
    rel: alternate
    isPlainText: true
    isHTML: false

# =============================================================================
# Page Configuration
# =============================================================================
# Correct page order on blog pages
page:
  nextPrevInSectionSortOrder: asc
  nextPrevSortOrder: asc

# =============================================================================
# Permalinks
# =============================================================================
# Configures permanent URLs for your content.
#
# WARNING: Do not copy the example below for a personal blog. The sectionslugs
# setting is used here to manage documentation URLs and requires a slug on every
# page. Either delete this section to use Hugo defaults, or use '/:slugorcontentbasename/'.
# See https://gohugo.io/configuration/permalinks/
# =============================================================================
permalinks:
  page:
    docs: /:sectionslugs/:slug/
    docs/shortcodes: /:sectionslugs/:slug/
  section:
    docs: /:sectionslugs/
    docs/shortcodes: /:sectionslugs/:slug/

# =============================================================================
# Markup Configuration
# =============================================================================
# Rules for converting Markdown to HTML
# [advanced] Pre-tuned defaults, no changes needed for most users.
markup:
  highlight:
    noClasses: false
  tableOfContents:
    startLevel: 2
    endLevel: 4
  goldmark:
    parser:
      wrapStandAloneImageWithinParagraph: false
      attribute:
        block: true
    renderer:
      unsafe: true
    extensions:
      passthrough:
        enable: true
        delimiters:
          block:
            - ['\[', '\]']
            - ['$$', '$$']
          inline:
            - ['\(', '\)']
      typographer:
        apostrophe: "'"
        leftDoubleQuote: '"'
        leftSingleQuote: "'"
        rightDoubleQuote: '"'
        rightSingleQuote: "'"

# =============================================================================
# Theme Parameters
# =============================================================================
params:
  logo: /img/logo.svg
  layout: 3-col # 2-col | 3-col

  # Theme
  themeColorScheme: latex # avocado | blowfish | congo | fire | latex | one-light | wood
  themeLightDarkMode: light # light | dark
  themeLightDarkSwitcher: true

  # Image
  imageFeatured: /img/07.webp
  imageSocial: /img/07.webp
  # imagePosition: 50% 50% # same as mozilla object-position
  imageOptimization: true
  imageOptimizationMD: true
  imageLightbox: true
  imageHotlink: false

  # search
  searchEnabled: true
  searchPreload: true

  # Homepage
  homepageLayout: custom # background | card | classic | editorial | matrix | mono | monument | plain | split | void
  homepageTitle: Hugo Theme Yore
  homepageImage: /img/07.webp
  homepageShowMoreLink: docs
  homepageTagline: |
    A feature rich yet clean theme
    focus on reading
  homepageSubTagline: |
    Between Text and Thought
    Exploring the Possibilities of Deep Reading

  # Header
  headerLayout: hideOnScroll # sticky | static | hideOnScroll
  headerShowTitle: false

  # Repo
  repoURL: https://github.com/ZhenShuo2021/hugo-yore/blob/main  # Base URL to branch root
  repoSubdir: exampleSite # Path from the repository root to the Hugo project directory. Leave empty if the site is in the root directory.

  # Page
  pageHeroStyle: disable # background | big | disable
  pageShowSeries: both # top | bottom | both | disable
  pageShowMeta: true
  pageShowTags: true
  pageShowCategories: true
  pageShowNext: true
  pageShowRelated: true
  pageShowAuthors: true
  pageShowActions: true
  pageTOCStyle: top # top | sidebar | disable
  pageRelatedLimit: 3 # Maximum number of related articles

  # Docs
  # docsIcon: "xmark" # Icon added to the docs nav bar, can be set in the front matter
  # docsIconClass: "foo bar" # Classes added to the docs icon to change, for example, color. Can be set in the front matter
  docsPageLoader: true
  docsAutoCollapseCategories: true

  # Section
  sectionQuickReference: false

  # These are parameters in https://gohugo.io/methods/pages/
  # sectionSortBy: Weight # Date | ExpiryDate | Lastmod | Length | LinkTitle | PublishDate | Title | Weight | Param.[FRONT_MATTER_KEY]
  # sectionSortOrder: asc # asc | desc
  # sectionGroupBy: Date # Date | ExpiryDate | Lastmod | PublishDate | Param.[FRONT_MATTER_KEY]
  # sectionGroupLayout: January 2006 # or "2006年一月" in zh-cn   https://gohugo.io/methods/pages/groupbyexpirydate/#layout-string
  # sectionGroupOrder: desc # asc | desc

  # Footer
  footerShowMenu: true
  footerShowCopyright: true
  footerShowCredit: true
  footerCopyrightText: Copyright © 2025 Yore. All rights reserved.

  # Misc
  accessibilityEnabled: true
  backlinkEnabled: true
  breadcrumb: true
  breadcrumbSchema: true
  codeCopy: true
  mathEnabled: false
  menuHighlight: true
  scrollToTop: true
  tocHighlight: true
  footnoteTooltip: true
  hugoTailwind: false
  versionSwitcher: false
  cookieConsent:
    enable: true
    categories:
      - necessary
      - functional
      - analytics
      - example_basic
      - example_social_media
      - example_marketing
      # - advertising
  # metaRobots: index, follow

# =============================================================================
# Languages Configuration
# =============================================================================
languages:
  # Language-specific configuration
  en:
    contentDir: content/en
    locale: en # the region subtag MUST be uppercase, e.g. en-US
    label: 🇺🇸 English
    direction: ltr
    weight: 1
    title: Yore
    params:
      description: A powerful, lightweight theme for Hugo.
    menus:
      # Header navigation links ordered by weight (lowest first).
      main:
        - name: Docs
          pageRef: docs
          weight: 10
          # pre: code  # add an icon named "code"

        # Nested menu example
        # - name: Introduction
        #   parent: Docs
        #   pageRef: docs/20-introduction
        #   weight: 10
        # - name: Reference
        #   parent: Docs
        #   pageRef: docs/994-reference-configuration
        #   weight: 20

        - name: Blog
          pageRef: /blog
          weight: 20

        # Icon links, no pageRef, must use an identifier
        - identifier: foo
          pre: github
          url: https://github.com/ZhenShuo2021/hugo-yore
          weight: 224

      # Bottom navigation links displayed before copyright.
      footer:
        - name: About
          pageRef: about
          weight: 1
        - name: Archive
          pageRef: archive
          weight: 5
        - name: Authors
          pageRef: authors
          weight: 7
        - name: Tags
          pageRef: tags
          weight: 10
        - name: Privacy
          pageRef: privacy
          weight: 15
        - name: RSS
          url: /index.xml
          weight: 20

  # 各種語言獨立的設定
  zh-cn:
    contentDir: content/zh-cn
    locale: zh-CN # the region subtag MUST be uppercase
    label: 🇨🇳 简体中文
    direction: ltr
    weight: 2
    title: Yore
    hasCJKLanguage: true
    params:
      description: 一个强大、轻量级的 Hugo 主题。
    menus:
      # 顶部导航链接按权重排序（最小值优先）。
      main:
        - name: 文档
          pageRef: docs
          weight: 10
          # pre: code  # 加入 "code" 圖標

        # 子菜單範例
        - name: Introduction
          parent: Docs
          pageRef: docs/20-introduction
          weight: 10
        - name: Reference
          parent: Docs
          pageRef: docs/994-reference-configuration
          weight: 20

        - name: Blog
          pageRef: /blog
          weight: 20

        # 图标链接，无 pageRef，必须使用 identifier
        - identifier: foo
          pre: github
          url: https://github.com/ZhenShuo2021/hugo-yore
          weight: 224

      # 显示在版权信息前的底部导航链接。
      footer:
        - name: 关于
          pageRef: about
          weight: 1
        - name: 归档
          pageRef: archive
          weight: 5
        - name: 作者
          pageRef: authors
          weight: 7
        - name: 标签
          pageRef: tags
          weight: 10
        - name: 隐私政策
          pageRef: privacy
          weight: 15
        - name: RSS
          url: /index.xml
          weight: 20

# dev server only. configure equivalent redirects on your production server
# See https://discourse.gohugo.io/t/404-in-multilingual-site/49273
# [advanced]
server:
  redirects:
    - from: /en/**
      status: 404
      to: /en/404.html
    - from: /zh-cn/**
      status: 404
      to: /zh-cn/404.html
```
