[under construction]

### Matrix cells

![A graylisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-1.png)

[Above] A graylisted cell. In this example, this means "everything from `arstechnica.com` will be blocked, except the main frame". The cell is pale red because it doesn't have an explicit rule attached to it, it inherits its blocked status from a higher precedence cell in the matrix.

![A graylisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-2.png)

[Above] A graylisted cell. In this example, this means "everything from `arstechnica.com` will be allowed". The cell is pale green because it doesn't have an explicit rule attached to it, it inherits its allowed status from a higher precedence cell in the matrix.

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

**Important note**: When you click the padlock tool, **all cells in the matrix** will have their state persisted using their current temporary status. This also applies to the scope cell at the top.

![A permanently whitelisted cell which is temporarly graylisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-6.png)

[Above] A permanently whitelisted cell which is temporarily graylisted. Remember, the effective status of a cell is its temporary status: all requests are evaluated against the temporary (effective) status.

![A permanently whitelisted cell which is temporarly blacklisted](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-7.png)

[Above] A permanently whitelisted cell which is temporarily blacklisted. Again, the temporary status is the one against which requests are evaluated, this means that all requests which destination is `arstechnica.com` will be blocked.

Once you have fiddled enough and want to clear temporary status for all cells to their natural permanent status, you click the "revert" icon in the toolbar (it's an eraser in case you wonder):

![A whitelisted cell](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-tools-revert-1.png)

Which means the above cell, used as an example, will go back to its natural (permanent) state:

![A permanently whitelisted cell in its default state](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/popupmenu-matrix-cell-5.png)

By the way, a cell without the top-left permanent indicator means that its persisted status is graylisted (the natural state of cells).