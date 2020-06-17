# Installation

$async is available on NPM as [@style.tools/async](https://npmjs.com/package/@style.tools/async) and as a PHP Composer package.

### Install via NPM

```bash
npm install @style.tools/async --save
```

Package: https://npmjs.com/package/@style.tools/async

### Install via PHP Composer

```bash
composer require styletools/async
```

Package: https://packagist.org/packages/styletools/async

# Usage

$async is modular and easy to use: select only the features that are needed to achieve the tiniest script size.
- simply stitch pre-optimized GCC modules together for a performant IIFE. You can wrap the modules in [dist/](./dist/) into an IIFE, e.g. `!function(){/* stitched modules */}();`. Follow the module order in [package.json](./package.json).
- [Online IIFE generator](https://style.tools/iife/) (adds an extra GCC _Advanced mode_ compression layer)
- [Node.js/CLI IIFE generator](https://github.com/style-tools/async-iife) (adds an extra GCC _Advanced mode_ compression layer)
- PHP IIFE generator (available on request: info@style.tools)

# IIFE Generator

[$async IIFE generator](https://github.com/style-tools/async-iife) enables to easily create a pre-concatenated selection of `$async` modules that is additionally optimized using [Google Closure Compiler](https://developers.google.com/closure/compiler/). 

The IIFE generator is available online on [https://style.tools/iife/](https://style.tools/iife/).

- [IIFE Generator documentation](./iife-generator.md)

# Module concatenation: select only what you use

$async is compiled into modules via [Google Closure Compiler](https://developers.google.com/closure/compiler/) that does not just compress javascript but also [optimizes it for speed](https://developers.google.com/closure/compiler/).

The Google Closure Compiler module architecture enables to concatenated a selection of $async modules without the use of a module loader. You can simply wrap the module source text in a IIFE and include it safely in the HTML document.

## Example: Pre-concatenated file

```html
<script async src="js/async-iife.js" data-c='[
   [
      "css/sheet1.css",
      {
         "href": "https://cdn.com/css/sheet2.css",
         "render_timing": "requestAnimationFrame"
      }
   ]
]'></script>
```

## Example: Inline concatenation

```php
<?php

// include a selection of $async modules inline
echo "<script>(function(){"; // wrap in IIFE
readfile('vendor/styletools/async/dist/async-core.js');
readfile('vendor/styletools/async/dist/css-loader.js'); 
readfile('vendor/styletools/async/dist/cache.js'); // cache module
readfile('vendor/styletools/async/dist/localstorage.js'); // localStorage module
echo "})();</script>";
?>
```
