A matrix scope tells HTTPSB which set of rules to use when visiting a particular web page. There are three levels of scope in HTTPSB:

![Scopes](https://raw2.github.com/gorhill/httpswitchboard/b80b342b153c0921feef9f9d0b700942bed80aff/doc/img/about-scopes-1.png)

Global scope -- identified as `*` (this scope is always present):
- All rules in the global scope apply to all web pages for which no narrower scope exists.

Domain-level scope (example above: `*.arstechnica.com`):
- Rules in a domain-level scope apply only to web pages which URL match the domain of the page.

Site-level scope (example: `arstechnica.com`)
- Rules in a site-level scope apply only to web pages which URL match the hostname of the page.

Out of the box, there are two scopes in HTTPSB: the global scope (`*`), and the behind-the-scene scope (`chromium-behind-the-scene`).

For any web page you visit, you can create a narrower scope for that web page, or use the default global scope.

Just to avoid any confusion in the context of this doc, "domain name" is different than "site name". For example, `example.com` is a domain name, whereas `www.example.com` and `forums.example.com` are site names.

### Global scope

The global scope is identified with the `∗` glyph.

Rules in global scope will apply to any web site, except where a narrower scope exists for that site.

### Domain-level scope

Domain-level scopes are narrower than global scope, but broader than site-level scopes.

Rules in domain-level scope will apply *only* to web sites which domain matches the domain of the scope.

For example, all rules in domain-level scope `∗.example.com` will apply to `www.example.com`, `forums.example.com`, `where.am.i.example.com`, etc.

### Site-level scope

Rules in site-level scope will apply *only* to web sites which hostname matches exactly the hostname of the scope.

Site-level scopes are the most narrow of all level of scopes. Rules in a site-level scope will apply only to *one* single web site.

For example, all rules in site-level scope `example.com` will apply to `example.com` only, and not to `forums.example.com` or `www.example.com`.

### Scope precedence

There is a scope precedence in HTTPSB. If one scope doesn't exist, a scope with lower precedence is then tried, until global scope is reached.

If one visits `www.example.com`, the precedence is:

    www.example.com
    *.example.com
    *