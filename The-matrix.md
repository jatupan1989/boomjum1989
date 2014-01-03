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
    * If a nostname is blacklisted (dark red), requests for top web pages for that hostname will be cancelled, which means nothing will download from that hostname since the top web page contains everything else.
- The top-left cell lets you control all the other cells in the matrix.
    * A click on that single cell allows you to whitelist or blacklist all the cells in the matrix -- **except** those cells which are explicitly white or blacklisted.
    * This cell affects the status of graylisted cells in the top row and the left-most column.
    * In turn, the cells in the top row affect the status of graylisted cells under them.
    * In turn, the cells in the left-most column affect the status of graylisted cells on their right.