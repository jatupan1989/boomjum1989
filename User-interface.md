[under construction]

### Matrix toolbar

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-1.png)

From left to right:
* Scope selector.
    - Default is global scope: `*`. In global scope mode, rules apply to all web pages, except those which match a narrower scope.
    - Other scopes:
        * Domain-level scope. Example: `https://*.google.com`. Rules at domain-level scope will apply to web pages which match the scope, including the scheme (`https` or `http`), except if for web pages which match an even narrower scope.
        * Site-level scope. Example: `https://www.facebook.com`. Rules at site-level scope will apply to web pages which match *exactly* the name of the scope, including the scheme.
    - An example for the use of scopes: block `facebook.com` globally, but allow `facebook.com` when visiting `https://www.facebook.com`. This is useful to prevent those ubiquitous servers from tracking you, unless you explicitly visit them.
    - Another example: to enforce the use of a secure scheme for a web site. If you create a scope `https://www.google.com` along with specific rules, these rules will *not* apply of the visited web page is `http://www.google.com`.

    