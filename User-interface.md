[under construction]

### Badge
![Extension badge](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-badge-1.png)

The green/red coloured areas in the icon give an overview of how many requests were allowed (green) versus how many were blocked.

The number in the icon represents the total number of *distinct* requests made -- successfully or not -- by the web page. Blocked or allowed requests are counted the same.

The background color of the number indicates the current scope being in effect.
    - Black: global scope.
    - Dark blue: domain-level scope.
    - Light blue: site-level scope.

### Matrix toolbar

![Matrix toolbar](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-toolbar-1.png)

From left to right:
* Scope selector:
    - Default is global scope: `*`. In global scope mode, rules apply to all web pages, except those which match a narrower scope.
    - Other scopes:
        * Domain-level scope.
            - Example: `https://*.google.com`. Rules at domain-level scope will apply to web pages which match the scope, including the scheme (`https` or `http`), except if for web pages which match an even narrower scope.
        * Site-level scope.
            - Example: `https://www.facebook.com`. Rules at site-level scope will apply to web pages which match *exactly* the name of the scope, including the scheme.
    - An example for the use of scopes: block `facebook.com` globally, but allow `facebook.com` when visiting `https://www.facebook.com`. This is useful to prevent those ubiquitous servers from tracking you, unless you explicitly visit them.
    - Another example: to enforce the use of a secure scheme for a web site. If you create a scope `https://www.google.com` along with specific rules, these rules will *not* apply if the visited web page is `http://www.google.com`.
* Padlock: for any changes to be permanent, you need to click the padlock.
    - All changes in the matrix are temporary by default. This applies to scope selection as well.
    - Don't be scared to experiment with whitelisting, blacklisting or graylisting. It's all temporary.
    - When you are satisfied with the state of the matrix, make the scope/rules permanent by clicking the padlock.
* Force a reload the web page.
    - The web page will reload if needed when you close the popup menu, but you can force a reload while the popup menu is opened in order to see the effects of your changes.
* Revert all rules.
    - Clicking this button will cause all temporary rules to be wiped out. Only the permanent rules will be active in the matrix.
* Last button is to bring up more options, which are explained below.
    