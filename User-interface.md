[under construction]

### Badge
![Extension badge](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-badge-1.png)

The green/red coloured areas in the icon give an overview of how many requests were allowed (green) versus how many were blocked (red).

The number in the icon represents the total number of *distinct* requests made -- successfully or not -- by the web page. Blocked or allowed requests are counted the same.

The background color of the request count indicates the current scope (see below) being in effect:

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

### Matrix

![Matrix: the "all" cell](https://raw.github.com/gorhill/httpswitchboard/fe5030c69e2185d703a1313fcd9d25444c4b209c/doc/img/popupmenu-matrix-all-1.gif)

A quick overview of the matrix:
- The matrix is made of cells.
    * Each cell is bound to a hostname, a type of request, or both.
- A greenish cell (pale or dark) represents a request to allow.
    * Dark green means there is an explicit whitelist rule assigned to the cell.
    * Pale green means the whitelist status is inherited from another higher precedence cell in the matrix.
- A reddish cell (pale or dark) represents a request to block.
    * Dark red means there is an explicit blacklist rule assigned to the cell.
    * Pale red means the blacklist status is inherited from another higher precedence cell in the matrix.
- A pale green or pale red cell is also referred to as being *graylisted*.
    * A graylisted cell always inherit its whitelist or blacklist status from an higher precedence cell.
- The top row lets you control the types of request which are to be allowed/denied.
- The left-most column lets you control the hostnames which are to be allowed/denied.
- The top-left cell lets you control all the other cells in the matrix.
    * A click on that single cell allows you to whitelist or blacklist all the cells in the matrix -- **except** those cells which are explicitly white or blacklisted.
    * This cell affects the status of graylisted cells in the top row and the left-most column.
    * In turn, the cells in the top row affect the status of graylisted cells under them.
    * In turn, the cells in the left-most column affect the status of graylisted cells on their right.

### Matrix cells

...

- ![Graylisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-1.png) : A graylisted cell. In this example, this means "everything from `arstechnica.com` will be blocked". The cell is pale red because it doesn't have an explicit rule attached to it, it inherit its blacklist status from a higher precedence cell in the matrix.
-