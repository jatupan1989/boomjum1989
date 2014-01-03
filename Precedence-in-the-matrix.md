The defining features of *HTTP Switchboard* are the precedence/graylisting/inheritance concepts in the matrix.

A "graylisted" matrix cell (pale green or pale red) means the cell inherits its allow or block status from a higher precedence cell in the matrix.

This feature allows the user to whitelist or blacklist a whole group of cells with a single click on a higher precedence cell in the matrix. Here is the tree list of precedence/inheritance in the matrix, from highest to lowest:

- The `all` cell (top-left corner of the matrix)
    * Types cells (i.e. `cookie`, `css`, `img`, etc.)
        - Specific type and specific domain names (i.e. `css/wikipedia.org`, `img/wired.com`, etc.)
            * Specific type and specific subdomain names (i.e. `css/en.wikipedia.org`, `script/www.facebook.com`, etc.)
    * Domain name cells (i.e. `wikipedia.org`, `facebook.com`, `wired.com`, etc.)
        - Specific type and specific domain names (i.e. `css/wikipedia.org`, `img/wired.com`, etc.)
            * Specific type and specific subdomain names (i.e. `css/en.wikipedia.org`, `script/www.facebook.com`, etc.)
        - Subdomain name cells (i.e. `en.wikipedia.org`, `www.facebook.com`, `video.wired.com`, etc.)
            * Specific type and specific subdomain names (i.e. `css/en.wikipedia.org`, `script/www.facebook.com`, etc.)

Any explicit whitelist or blacklist status of a cell will cascade down through inheritance to the **graylisted** cells in the level underneath. Ultimately, this means that it is possible to control all the cells in the matrix with just the top-left `all` cell (assuming all cells in the matrix are graylisted).

Now if you've understood the above tree list, you may have noticed that a single graylisted cell in the middle of the matrix may inherit from two different ancestors: the hostnames (left column) or the type (top row). It is up to the user to choose how this double inheritance works by disabling or enabling "strict blocking (on the *Settings* page):

!["Strict blocking" on and off](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/strict-blocking.gif)

- "Strict blocking" disabled: the hostname has precedence over the type, meaning if the hostname is whitelisted, the cell will inherit whitelist status even if the type is blacklisted.
- "Strict blocking" enabled: both the hostname and type have same precedence, meaning both must be whitelisted for the cell to inherit whitelist status.

"Strict blocking" is strongly recommended for security conscious users.

[to do: many animated GIF to illustrate the above]