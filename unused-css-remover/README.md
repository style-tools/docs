Style.Tools, a free [CSS optimization widget](../README.md), provides access to an advanced unused CSS remover and extractor.

The unused CSS remover uses the same technology as the Critical CSS generator and supports the same [UI actions](critical-css-generator/advanced-ui-actions.md) for Puppeteer-like browser control.

The unused CSS remover provides three output options:

1. remove unused CSS from a stylesheet
2. extract unused CSS into a new stylesheet
3. download

# Usage

The unused CSS remover provides two modes: `Simple` and `Advanced`.

## Simple mode

Simple mode applies the default configuration based on the viewport size and scroll position defined by the Critical CSS window.

## Advanced mode

Advanced mode provides many options for tuning the unused CSS remover and PostCSS parser. 

The configuration is 100% JSON and is available in a [JSON schema](https://style.tools/json-schemas/unused-css-remover.json).

# Configuration

By default, the unused CSS remover simply performs the unused CSS remover process on the basis of the active Critical CSS window.

```json
{
  "atRulesToKeep": [
    "charset",
    "keyframes",
    "import",
    "namespace",
    "page"
  ],
  "atRulesToRemove": [],
  "selectorsToKeep": [
    "*",
    "*:before",
    "*:after",
    "html",
    "body"
  ],
  "selectorsToRemove": [],
  "propertiesToKeep": [],
  "propertiesToRemove": [],
  "pseudoSelectorsToKeep": [
    "/:.*/"
  ],
  "pseudoSelectorsToRemove": [],
  "maxElementsToCheckPerSelector": false,
  "strictParser": false,
  "ui_actions": [
    {
      run: true
    }
  ]
}
```

The options enable to fine tune the PostCSS parser, what selectors and properties to preserve or to forcefully remove and the UI actions to perform during the unused CSS extraction process.

`ui_actions` accepts the same configuration as the Critical CSS generator. 

- [UI actions documentation](../critical-css-generator/advanced-ui-actions.md)


# Google Cloud based automation

[PageSpeed.PRO](https://pagespeed.pro) can provide the advanced Unused CSS remover as an **automated solution** based on Google Cloud infrastructure. 

For information, visit [https://pagespeed.pro/google-cdn/](https://pagespeed.pro/google-cdn/).

[![](../gitbook/images/psp-concept.jpg)](https://pagespeed.pro/)