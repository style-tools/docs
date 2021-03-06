# Advanced critical CSS generator

The configuration of the advanced critical CSS generator is 100% JSON and is availale in a [JSON schema](https://style.tools/json-schemas/critical-css-generator.json).

# Options

| Option                         | Description     | Type     |
|--------------------------------|-----------------|----------|
| `atRulesToKeep`     | An array of CSS `@` rules (string or regular expression) to forcefully include in the Critical CSS. | `["media", "charset", "/rule(.*)/i"]` |
| `atRulesToRemove`    | An array of CSS `@` rules (string or regular expression) to forcefully remove from the Critical CSS. | `["media", "charset", "/rule(.*)/i"]`   |
| `selectorsToKeep`      | An array of CSS selectors (string or regular expression) to forcefully include in the Critical CSS. | `[".selector", "/\\.selector(.*)/i"]` |
| `selectorsToRemove`      | An array of CSS selectors (string or regular expression) to forcefully remove from the Critical CSS. | `[".selector", "/\\.selector(.*)/i"]` |
| `propertiesToKeep`      | An array of CSS declarations (string or regular expression) to forcefully include in the Critical CSS. To match values, use a 2nd level array with the declaration string or regex at index 0 and the value string or regex at index 1. | `["-webkit-transition", "/(.*)transition(.*)/i", [ "display", "none" ] ]` |
| `propertiesToRemove`      | An array of CSS declarations (string or regular expression) to forcefully remove from the Critical CSS. To match values, use a 2nd level array with the declaration string or regex at index 0 and the value string or regex at index 1. | `["-webkit-transition", "/(.*)transition(.*)/i", [ "display", "none" ] ]` |
| `pseudoSelectorsToKeep`      | An array of CSS pseudo selectors (string or regular expression) to forcefully include in the Critical CSS. | `[":before", "/:nth-child(.*)/i"]` |
| `pseudoSelectorsToRemove`      | An array of CSS pseudo selectors (string or regular expression) to forcefully remove from the Critical CSS. | `[":before", "/:nth-child(.*)/i"]` |
| `maxElementsToCheckPerSelector`   | A maximum amount of elements to check for above the fold visibility. This setting can impact the speed of the generator. | `false` or `100` |
| `maxEmbeddedBase64Length`   | The maximum size in bytes of Base64 encoded inline images to include in the Critical CSS. | `1000`  |
| `strictParser`   | By default, the CSS is parsed using the fault tolerant [PostCSS Safe Parser](https://github.com/postcss/postcss-safe-parser) that automatically fixes syntax errors. This setting enables to use the strict parser. |  `true`  |
| `ui_actions`   | An array of actions to perform on the UI state to discover above-the-fold CSS code. | `[{"viewport":"360x640"}, {"run": true}]` |

# Example configuration

```json
{
  "atRulesToKeep": [],
  "atRulesToRemove": [],
  "selectorsToKeep": [
    "*",
    "*:before",
    "*:after",
    "html",
    "body"
  ],
  "selectorsToRemove": [
    "/\\#C/",
    "/\\.chattxt/"
  ],
  "propertiesToKeep": [],
  "propertiesToRemove": [
    "/(.*)transition(.*)/i",
    "cursor",
    "pointer-events",
    "/(-webkit-)?tap-highlight-color/i",
    "/(.*)user-select/i"
  ],
  "pseudoSelectorsToKeep": [
    "::before",
    "::after",
    "::first-letter",
    "::first-line",
    ":before",
    ":after",
    ":first-letter",
    ":first-line",
    ":visited",
    "/:nth-child.*/"
  ],
  "pseudoSelectorsToRemove": [],
  "maxElementsToCheckPerSelector": false,
  "maxEmbeddedBase64Length": 1000,
  "strictParser": false,
  "ui_actions": [
    {
      "viewport": "360x640",
      "notes": "Set viewport for above-the-fold CSS discovery."
    },
    {
      "wait": 1000,
      "notes": "wait for 1000ms to enable the viewport to render."
    },
    {
      "run": true,
      "notes": "Run critical CSS generator (above-the-fold CSS calculation)"
    },
    {
      "mouseevent": "click",
      "selector": "a.nav-menu",
      "notes": "Fire new MouseEvent on a.nav-menu DOM element."
    },
    {
      "wait": 2000
    },
    {
      "run": true
    },
    {
      "script": "close_nav_menu();",
      "notes": "Execute a script, in this case close the menu before continuing with next viewport."
    },
    {
      "viewport": "1300x900"
    },
    {
      "wait": 1000
    },
    {
      "run": true
    }
  ]
}
```

# Setup

Start the 📐 Style.Tools browser widget (see [introduction](../README.md)) and click on `Tools` (top) and `Critical CSS Generator` (menu-item).

![Critical CSS menu](../gitbook/images/critical-css-menu.png)

Select `Advanced mode` and configure the JSON using the options mentioned above.

![Critical CSS generator configuration](../gitbook/images/critical-css-generator-config.png)

The generator provides three output options:

1. replace the critical CSS `<style>` element
2. append to the critical CSS `<style>` element
3. download

Click the extract button to start the generator.

# Optimizing the result

The output of the Critical CSS generator is raw and requires further optimization such as compression.

The critical CSS will contain a comment with basic statistics. In the example below for [www.w3schools.com](https://www.w3schools.com/), the critical CSS output has a size of 29.69 kB, a reduction of 73.07% from the original CSS.

![Raw Critical CSS output](../gitbook/images/critical-css-after-generation.png)

The `Optimize` button in the editor menu enables to apply code optimization and compression. As you can see in the example below, the optimization further reduced the size to 15.87 kB, a reduction of 48.70% from the raw Critical CSS.

![Optimized Critical CSS](../gitbook/images/critical-css-result-after-optimize.png)

# Above the fold optimization

By comparing the Critical CSS View with the Original CSS View you can detect issues with the Critical CSS and optimize the critical CSS manually to achieve a pixel perfect result.

![Above the fold optimization](../gitbook/images/critical-css-generator-abtf.png)

# UI actions

The advanced critical CSS generator provides Puppeteer-like browser control and enables to execute scripts, trigger events such as `mouseover`, control the scroll position and viewport size and more.

UI actions enables the critical CSS generator to provide a 100% accurate and reliable result.

- [UI actions documentation](./advanced-ui-actions.md)

[![](../gitbook/images/psp-concept.jpg)](https://pagespeed.pro/)