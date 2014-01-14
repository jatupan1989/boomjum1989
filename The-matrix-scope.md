A matrix scope tells HTTPSB which ruleset to use when visiting a particular web page. There are three levels of scope in HTTPSB:

![Scopes](https://raw2.github.com/gorhill/httpswitchboard/b80b342b153c0921feef9f9d0b700942bed80aff/doc/img/about-scopes-1.png)

- Global scope -- identified as `*` (this scope is always present)
- Domain-level scope (example above: `http://*.arstechnica.com`)
- Site-level scope (example: `http://arstechnica.com`)

