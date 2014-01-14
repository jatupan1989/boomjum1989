A matrix scope tells HTTPSB which set of rules to use when visiting a particular web page. There are three levels of scope in HTTPSB:

![Scopes](https://raw2.github.com/gorhill/httpswitchboard/b80b342b153c0921feef9f9d0b700942bed80aff/doc/img/about-scopes-1.png)

- Global scope -- identified as `*` (this scope is always present)
    * All rules in the global scope apply to all web pages for which no narrower scope exists.
- Domain-level scope (example above: `http://*.arstechnica.com`)
    * Rules in a domain-level scope apply only to web pages which URL match the domain of the page.
- Site-level scope (example: `http://arstechnica.com`)
    * Rules in a site-level scope apply only to web pages which URL match the hostname of the page.

Out of the box, there are two scopes in HTTPSB: the global scope (`*`), and the behind-the-scene scope (`http://chromium-behind-the-scene`).

For any web page you visit, you can pick create a narrower scope for that web page, or use the default global scope.

### Global scope

### Domain-level scope

### Site-level scope