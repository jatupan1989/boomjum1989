So far, here is what I found:

- [favicon.ico](http://en.wikipedia.org/wiki/Favicon)
- [web fonts](http://en.wikipedia.org/wiki/Web_fonts)
- HTML5 [&lt;audio&gt;](http://en.wikipedia.org/wiki/HTML5_Audio) tag
- HTML5 [&lt;video&gt;](http://en.wikipedia.org/wiki/HTML5_video) tag
- [SVG](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) files
- [WebSocket](https://en.wikipedia.org/wiki/WebSocket)
- I found a behind-the-scene request occurrence by chromium: <https://www.google.com/searchdomaincheck?format=url&type=chrome>
- Since [version 0.6.6](https://github.com/gorhill/httpswitchboard/wiki/Change-log#066), stylesheets (`.css` files) from third-party domains are reported in the `other` column:
    * A "third-party domain" is defined as a domain which doesn't match the domain of the URL address of the page loaded in your browser.
