---
title: "Cookie Consent"
slug: "cookie-consent"
description:
weight: 140
date: 2026-03-28T18:00:00+08:00
tags: ["cookie", "gdpr", "privacy", "configuration", "documentation"]
series: ["Documentation"]
series_weight: 140
sites:
  matrix:
    versions: '>= v2.0.0'
---

Yore integrates [vanilla-cookieconsent][lib] for GDPR-compliant cookie management. Built-in categories are `necessary`, `functional`, `analytics`, and `advertising`.

> [!IMPORTANT]
> 1. Google Ads related products are [not compatible](https://github.com/orestbida/cookieconsent/issues/562) with vanilla-cookieconsent.
> 2. Most libraries exclude functional cookies such as dark mode from consent handling and [do not use the consent modal](https://github.com/themesberg/flowbite-react/issues/546#issuecomment-1385626284). Yore follows the same behavior and does not manage them.
> 3. Provide a cookie settings entry accessible from all pages to meet GDPR requirements.

## Configuration

```yaml {title="hugo.yaml"}
params:
  cookieConsent:
    enable: true
    categories:
      - necessary
      - functional
      - analytics
      - advertising
```

`categories` defines the available consent categories. To create a new category, add `NEW_CATEGORY` to `categories` and [override][override] `assets/cookie-translations/[LANG].json` to define the corresponding i18n fields.

## Preferences Button

The `cookie-settings` shortcode renders a button that opens the preferences modal.

```go-html-template
```

## Examples

### Scripts Management

Setting `type="text/plain"` on a script tag prevents it from executing. Adding `data-category` tells vanilla-cookieconsent to execute it when the user accepts that category.

```html {title="layouts/_partials/extend-head.html"}
<!-- gtag example -->
<script type="text/plain" data-category="analytics"
  data-src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXX"></script>
<script type="text/plain" data-category="analytics">
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXX');
</script>
```

### Execute code on consent

[`cc:onConsent`][onConsent] fires on every page load once consent is valid. [`cc:onChange`][onChange] fires when the user modifies their preferences.

[onConsent]: https://cookieconsent.orestbida.com/advanced/callbacks-events.html#onconsent
[onChange]: https://cookieconsent.orestbida.com/advanced/callbacks-events.html#onchange

```js
window.addEventListener('cc:onConsent', () => {
  if (window.CookieConsent.acceptedCategory('analytics')) {
    // initialize analytics
  }
});

window.addEventListener('cc:onChange', ({ detail }) => {
  if (detail.changedCategories.includes('analytics')) {
    if (window.CookieConsent.acceptedCategory('analytics')) {
      // re-enabled
    } else {
      // disabled
    }
  }
});
```

## Advanced

### API

Yore detects `assets/js/cookie-consent-config.js` and calls the exported function before `CookieConsent.run()`.

```js {title="assets/js/cookie-consent-config.js"}
export default function ({ addCategory }) {
  // register additional categories here
}
```

#### addCategory

`addCategory` provide an advanced way to register and manage cookies. It registers a [category](https://cookieconsent.orestbida.com/essential/getting-started.html#configuration). For example, you can register set [autoClear](https://cookieconsent.orestbida.com/reference/configuration-reference.html#category-autoclear) to clear cookies when the user rejects the cookie category.

| Parameter | Description |
|-----------|-------------|
| `name` | Category identifier, referenced in `data-category` attributes |
| `categoryConfig` | Passed directly to vanilla-cookieconsent. See the [category config reference](https://cookieconsent.orestbida.com/reference/configuration-reference.html#categories) |
| `section` | `{ title, description }` displayed in the preferences modal |

**Example: Register a custom category**

```js {title="assets/js/cookie-consent-config.js"}
export default function ({ addCategory }) {
  addCategory(
    'advertising',
    {
      autoClear: {
        cookies: [{ name: /^(_fbp|_gcl)/ }],
      },
    },
    {
      title: 'Advertising',
      description: 'Cookies used to deliver personalized ads.',
    },
  );
}
```

### Override Template

Create `assets/js/cookie-consent.js` in your project to [override][override] the theme's file entirely, this is useful when you need full access to vanilla-cookieconsent hooks. Refer to the [vanilla-cookieconsent documentation][lib] for all available options.

[lib]: https://cookieconsent.orestbida.com/
[override]: ../../80-advanced/950-customization/index.md#override-templates
