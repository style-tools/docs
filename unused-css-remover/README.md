The Style.Tools [CSS optimization widget](./README.md) provides access an advanced unused CSS extractor and remover.

The unused CSS remover can extract and output unused CSS or remove unused CSS from a stylesheet.

The unused CSS remover uses the same technology as the Critical CSS generator and supports the same [UI actions](critical-css-generator/advanced-ui-actions.md).

![Google Lighthouse unused CSS penalty](../gitbook/images/lighthouse-unused-css-penalty.png)

# Usage

The unused CSS remover provides two modes: `Simple` and `Advanced`.

# Simple mode

Simple mode applies the default configuration based on the viewport size and scroll position defined by the Critical CSS window.

# Advanced mode

Advanced mode provides many options for tuning the unused CSS remover and PostCSS parser. The configuration of the unused CSS remover is available in a [JSON schema](https://style.tools/json-schemas/unused-css-remover.json).

## Configuration

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

The options enable to fine tune the PostCSS parser, what selectors and properties to preserve or to forcefully remove and the UI actions to perform during the unused CSS removal process.

`ui_actions` accepts the same configuration as the UI actions of the Critical CSS generator. 

- [UI actions documentation](./advanced-ui-actions.md)