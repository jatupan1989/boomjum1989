A defining feature of *HTTP Switchboard* is the precedence/graylisting/inheritance concept in the matrix.

A "graylisted" matrix cell (pale green or pale red) means the cell inherits its allow or block status from a higher precedence cell in the matrix.

This feature allows the user to whitelist or blacklist a whole group of cell with a single click on a higher precedence cell in the matrix. Here is the tree list of precedence/inheritance of the matrix:

- The `all` cell (top-left corner of the matrix)
    * Types cells (`cookie`, `css`, `img`, etc.)
        - Specific type and specific domain names
            * Specific type and specific subdomain names
    * Domain name cells (`wikipedia.org`, `facebook.com`, `wired.com`, etc.)
        - Subdomain name cells (`en.wikipedia.org`, `www.facebook.com`, `video.wired.com`, etc.)
            * Specific type and specific subdomain names
        - Specific type and specific domain names
            * Specific type and specific subdomain names
