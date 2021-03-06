Style.Tools, a free [CSS optimization widget](../README.md), provides access to two Critical CSS generators: Simple and Advanced.

![Critical CSS extract](../gitbook/images/critical-css-extract.gif)

# Simple generator

The simple Critical CSS generator is based on a browser-trick that was originally [published](https://gist.github.com/PaulKinlan/6284142) by Google engineer Paul Kinlan. The snippet uses a Chrome innovation called `getMatchedCSSRules` that was deprecated and has been removed since Chrome 63.

The simple Critical CSS generator uses an enhanced version of the snippet and supports modern browsers via a [polyfill](https://github.com/ovaldi/getMatchedCSSRules) for `getMatchedCSSRules`. An added feature is the ability to set the viewport to support responsive designs.

The quality of the simple critical CSS generator is often not that well but it can provide a quick extract.

# Advanced generator

The advanced Critical CSS generator is based on [PostCSS](https://github.com/postcss/postcss) and can provide 100% accuracy for complex designs. The generator provides Puppeteer-like browser control that enables to discover CSS that may be applicable by browser activity such as scripts, events and scrolling.

## JSON configuration

The advanced generator is 100% JSON controlled which enables to easily re-use configuration so that in practice, an advanced extract of critical CSS can be done in a few seconds.

## The best result

The Style.Tools Critical CSS generator is custom developed and provides a much better result than the leading open source tools such as [Penthouse.js](https://github.com/pocketjoso/penthouse/) and [Critical](https://github.com/addyosmani/critical). 

The generator goes a few steps further than Penthouse.js. It uses [PostCSS](https://github.com/postcss/postcss) instead of [csstree](https://github.com/csstree/csstree) for improved CSS parsing (for example: it accepts malformed CSS) and it is enhanced in many ways to provide a more accurate result.

## Raw unfiltered output: pure critical CSS

What makes the generator truly different is that it outputs pure and unfiltered Critical CSS and does not apply any compression or optimization techniques. The output of the generator is thereby reliable. No CSS code goes missing without the control of the configuration.

Professional CSS code optimization solutions such as [clean-css](https://github.com/jakubpawlowicz/clean-css) are also available in the CSS optimization widget and can provide perfect quality code optimization and compression. The final result is thereby better (better compression and more accurate) than that of other tools.

- [View usage documentation](./advanced-usage.md)
- [View UI actions documentation](./advanced-usage.md)

# Google Cloud based automation

[PageSpeed.PRO](https://pagespeed.pro) can provide the advanced Critical CSS generator as an **automated solution** based on Google Cloud infrastructure. 

For information, visit [https://pagespeed.pro/google-cdn/](https://pagespeed.pro/google-cdn/).

[![](../gitbook/images/psp-concept.jpg)](https://pagespeed.pro/)