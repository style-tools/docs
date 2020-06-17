The [Style.Tools](https://style.tools/) project started as a free browser-widget that provides a sort of DevTools (developer tools) for frontend optimization (FEO).

Style.Tools is available with 1 click **on any page on the internet**, including pages behind a login.

![Style.Tools CSS optimization widget](../gitbook/images/styletools-widget.gif)

Style.Tools provides access to advanced technologies for CSS optimization including:

- CSS editor with themes
- Critical CSS generator
- Unused CSS extractor and remover
- Duplicate CSS extractor and remover (unique innovation)
- CSS beautify
- CSS code optimization ([clean-css](https://github.com/jakubpawlowicz/clean-css))
- CSS code repair (fix malformed CSS)
- CSS lint (quality checks)
- CSS statistics (analysis)
- [PostCSS](https://github.com/postcss/postcss) plugins: autoprefixer and many more
- Above-the-fold optimizer

The widget provides **localhost and offline support** via a Service Worker on domain [style.tools](https://style.tools/). You can use many of the features locally without an internet connection. The cache for preferences is also preserved across domains which makes it efficient when working on multiple websites.

# Installation

The widget is a small piece of Javascript code that can be added to the browser bookmarks or favorites bar via the URL prefix `javascript:`.

```javascript
javascript:(function(r,a,k,l,f,g,b,m){function n(c,b,d){a.open();b&&(r.onmessage=b);d&&a.addEventListener("securitypolicyviolation",d);a.write(c);a.close()}f="https://style.tools/";g="Style.Tools";var c=a.createElement("script");c.src=f+"x.js";c.onerror=function(){function p(d){if(c=d?d.violatedDirective:0){if("script-src"==c||m)return;m=1;b&&l(b)}if(!q){var h=f+"#"+a.location;a.getElementById("e").innerHTML='<h2 style="color:red;">'+g+(c?' blocked by CSP <font color="blue">'+c+"</font>":" failed to load")+
'.</h2><h3>Redirecting <a href="'+h+'">'+h+"</a>...</h3>";b=k(function(){a.location.href=h},3E3)}}var q;n("<h2>Loading "+g+" via Service Worker...</h2><iframe src="+f+'go height=50></iframe><p id="e"></p>',function(a){q=1;b&&l(b);n("<script>"+a.data+"\x3c/script>")},p);b=k(p,2E3)};a.head.appendChild(c)})(window,document,setTimeout,clearTimeout);
```

![Add a new bookmark](../gitbook/images/add-bookmark.png)

Source of widget:
https://github.com/style-tools/widget/blob/master/widget.js (849 Bytes)

Visit [https://style.tools/](https://style.tools) for instructions and a easy *drag&drop link* to install the widget.


# CMS integration and plugins

Style.Tools is integrated in professional optimization libraries and CMS plugins including a [WordPress FEO plugin](https://pagespeed.pro/wordpress/) and a [Google CDN FEO solution](https://pagespeed.pro/google-cdn/). 

For information, see [https://pagespeed.pro/](https://pagespeed.pro/)

[![](../gitbook/images/psp-concept.jpg)](https://pagespeed.pro/)