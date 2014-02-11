![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-1.png)

### The scope selector

The scope selector let you choose where the rules you create apply.

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-2.png)

There are three scope levels: global, domain-level, and site-level scope.

Default is currently global scope: `*`. In global scope mode, rules apply to all web pages, except those which match a narrower scope.

Domain-level scope:
- Example: `*.google.com`. Rules at domain-level scope will apply to web pages which match the scope, except if for web pages which match an even narrower scope.

Site-level scope:
- Example: `www.facebook.com`. Rules at site-level scope will apply to web pages which match *exactly* the name of the scope, including the scheme.

An example for the use of scopes: block `facebook.com` globally, but allow `facebook.com` when visiting `www.facebook.com`. This is useful to prevent those ubiquitous servers from tracking you, unless you explicitly visit them.

More on scopes: [The matrix scope](/gorhill/httpswitchboard/wiki/The-matrix-scope).

### Persist temporary rules

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-3.png)

Padlock: for any changes to be permanent, you need to click the padlock.
- All changes in the matrix are temporary by default. This applies to scope selection as well.
- Don't be scared to experiment with whitelisting, blacklisting or graylisting. It's all temporary.
- When you are satisfied with the state of the matrix, make the scope/rules permanent by clicking the padlock.

### The preset recipes

Starting with version 0.7.8.0, preset recipes were introduced in order to assist the user to easily apply the proper rules to the matrix in order to "unbreak" a web page.

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-4.png)

The feature is still beta, and of course writing preset recipes take time. Evebtually there will be enough preset recipes out to assist less geeky users of the extension.

### Remove temporary rules from current scope

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-5.png)

Clicking this button will cause all temporary rules to be wiped out. Only the permanent rules will be active in the matrix. (Note that prior to version 0.7.9.4, this icon was to remove *all* temporary scopes and rules.)

### Remove all temporary rules

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-6.png)

To remove *all* temporary rules, including those not appearing in the current matrix, click this icon.

### Force reload the web page

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-7.png)

Force a reload the web page.

The web page will reload **only** if needed when you close the popup menu, but you can force a reload while the popup menu is opened in order to see the effects of your changes.

### Rule manager, Statistics, Settings, etc.

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-8.png)

Last button is to bring up more options, which are explained elsewhere.

The _On/off_ button allows to quickly disengage HTTPSB filtering. The extension will still record and report requests, but it won't block anything.