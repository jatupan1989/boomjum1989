What of the defining feature of *HTTP Switchboard* are the precedence/graylisting/inheritance concepts in the matrix.

A "graylisted" matrix cell (pale green or pale red) means the cell will inherit its allow or block status from a higher precedence cell in the matrix. This feature allows the user to whitelist or blacklist a whole group of cell with a single click on a higher precedence cell in the matrix. Here is the tree list of precedence/inheritance of the matrix:

- The "all" cell (top-left corner of the matrix)
    * Types cells ("cookie", "css", "img", etc.)
        - Specific type and specific domain names
    * Domain name cells ("wikipedia.org", "facebook.com", "wired.com", etc.)
        - Subdomain name cells ("en.wikipedia.org", "www.facebook.com", "video.wired.com", etc.)