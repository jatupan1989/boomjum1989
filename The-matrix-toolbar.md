![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-1.png)

### The scope selector

The scope selector let you choose where the rules you create apply, or where they are removed from. There are three scope levels: global, domain-level, and site-level scope.

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-2.png)

- Default is global scope: `*`. In global scope mode, rules apply to all web pages, except those which match a narrower scope.
- Other scopes:
    * Domain-level scope.
        - Example: `https://*.google.com`. Rules at domain-level scope will apply to web pages which match the scope, including the scheme (`https` or `http`), except if for web pages which match an even narrower scope.
    * Site-level scope.
        - Example: `https://www.facebook.com`. Rules at site-level scope will apply to web pages which match *exactly* the name of the scope, including the scheme.
- An example for the use of scopes: block `facebook.com` globally, but allow `facebook.com` when visiting `https://www.facebook.com`. This is useful to prevent those ubiquitous servers from tracking you, unless you explicitly visit them.
- Another example: to enforce the use of a secure scheme for a web site. If you create a scope `https://www.google.com` along with specific rules, these rules will *not* apply if the visited web page is `http://www.google.com`.

### Persist temporary rules

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-3.png)

Padlock: for any changes to be permanent, you need to click the padlock.
- All changes in the matrix are temporary by default. This applies to scope selection as well.
- Don't be scared to experiment with whitelisting, blacklisting or graylisting. It's all temporary.
- When you are satisfied with the state of the matrix, make the scope/rules permanent by clicking the padlock.

### The preset recipes menu

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-4.png)

### Remove temporary rules from current matrix

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-5.png)

Clicking this button will cause all temporary rules to be wiped out. Only the permanent rules will be active in the matrix.

### Remove all temporary rules

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-6.png)

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-7.png)

Force a reload the web page.
- The web page will reload if needed when you close the popup menu, but you can force a reload while the popup menu is opened in order to see the effects of your changes.

### Rule manager, Statistics, Settings, etc.

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-8.png)

Last button is to bring up more options, which are explained elsewhere.
