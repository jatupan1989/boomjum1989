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

![A graylisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-1.png)

[Above] A graylisted cell. In this example, this means "everything from `arstechnica.com` will be blocked, except the main frame". The cell is pale red because it doesn't have an explicit rule attached to it, it inherits its blacklist status from a higher precedence cell in the matrix.

![A graylisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-2.png)

[Above] A graylisted cell. In this example, this means "everything from `arstechnica.com` will be allowed". The cell is pale green because it doesn't have an explicit rule attached to it, it inherits its whitelist status from a higher precedence cell in the matrix.

![A blacklisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-4.png)

[Above] A blacklisted cell. In this example, this means "everything from `arstechnica.com` will be blocked, *including* the main frame". The cell is dark red because it has an explicit blacklist rule attached to it. The blacklist status of this cell will affect graylisted cells with lower precedence in the matrix.

![A whitelisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-3.png)

[Above] A whitelisted cell. In this example, this means "everything from `arstechnica.com` will be allowed". The cell is dark green because it has an explicit whitelist rule attached to it. The whitelist status of this cell will affect graylisted cells with lower precedence in the matrix.

With one click on a cell, you can change its graylist, whitelist or blacklist status. **In HTTPSB, cell status are temporary by default**, meaning the changes will be lost when you quit the browser. This is by design, to encourage users to experiment and fiddle with the matrix without worrying about leaving behind clutters of unwanted rules.

In order to make the whitelist or blacklist status of a cell permanent, you must save its status. You do so by clicking the padlock icon in the toolbar [below]:

![A whitelisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-tools-save-1.png)

The permanent status of a cell (if any) appears in the top-left corner of the cell:

![A permanently whitelisted cell in its default state](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-5.png)

[Above] A permanently whitelisted cell in its default state. This means the temporary status of the cell is explicitly whitelisted, which reflects its permanent status.

![A permanently whitelisted cell which is temporarly graylisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-6.png)

[Above] A permanently whitelisted cell which is temporarily graylisted. Remember, the effective status of a cell is its temporary status: all requests are evaluated against the temporary (effective) status.

![A permanently whitelisted cell which is temporarly blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-7.png)

[Above] A permanently whitelisted cell which is temporarily blacklisted. Again, the temporary status is the one against which requests are evaluated, this means that all requests which destination is `arstechnica.com` will be blocked.

