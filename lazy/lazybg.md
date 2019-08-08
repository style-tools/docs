# Lazy loading of `background-image` in stylesheets

`dist/lazybg.js` enables to lazy load background images in stylesheets. It makes use of [CSS Variables](https://www.w3schools.com/css/css3_variables.asp) with a fallback for old browsers.

There are four options to resolve images:

1. manually define images via `:root {}` within the stylesheet
2. base64 encode image URLs
3. provide a JSON source list as resolver
4. provide a javascript function as resolver

```css
/* :root based pre-configured value */
:root {
  --z--lazy-img: url('/image.jpg');
}
footer {
  background-image: url('/image.jpg'); // old browsers
  background-image: var(--z-lazy-img, none);
}

/* base64 encoded value */
p#out-of-view {
  background-image: url('/image.jpg'); // old browsers
  background-image: var(--z-base64_value, none); /* note: requires character replacements, see documentation */
}

/* JSON object or javascript function based custom resolver */
div#out-of-view {
  background-image: url('/image.jpg'); // old browsers
  background-image: var(--z-custom-resolved, none); 
}
```

```html
<script src="dist/lazybg.js"></script>
<script>
// default: document.styleSheets
$lazybg(); 

// custom $lazy config
$lazybg(
  document.querySelectorAll('link[rel=stylesheet], style#other'),
  {
    observer: {
      threshold: 0,
      rootMargin: '100px'
    }
  }
); 

// custom JSON based resolver
$lazybg(
  0,0, // default config

  // resolver
  {
    "custom-resolved": "url('/image.jpg')"
  }
); 

// custom javascript based resolver
$lazybg(
  0,0, // default config

  // resolver
  function(key) {

    // resolve key "custon-resolved"
    return "url('/"+key+".jpg');"
  }
); 
</script>
```

## Base64 encoded image value

CSS variables are limited to `DOMString`. The following characters need to be replaced in a `base64` encoded value:

`/`: `—` 

`=`: `•`