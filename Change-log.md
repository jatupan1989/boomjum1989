### 0.1.6
- Now block inline script tags on top frame when scripts are blacklisted for this top frame (before only separate script files where prevented from being loaded/executed). Still need to look into this for subframes.

### 0.1.5
- Added ability to block whole page
- Blocked subframes (&lt;iframe&gt;, etc.) are now redirected to a safe page (so there is a visual to indicate blocking)
- In a new install page & images are whitelisted by default
- Now using <a href="http://www.google.com/fonts/specimen/Roboto+Condensed">Roboto Condensed font</a>, better suited for the matrix
- Reworked project structure and code in order to grow better

### 0.1.4
- Fine tuned local storage

### 0.1.3
- Using built-in community-built blacklists from:
    * <a href="http://pgl.yoyo.org/as/index.php">Peter Lowe's blacklist</a> => <a href="http://pgl.yoyo.org/as/serverlist.php?mimetype=plaintext">Ad server hostnames for blocking ads</a>
    * <a href="http://www.malwaredomainlist.com/">Malware Domain List</a> => <a href="http://www.malwaredomainlist.com/hostslist/hosts.txt">MalwareDomainList.com Hosts List</a>
- Trivial GUI improvements
- User-defined lists stored format now more similar to third party lists (newline-separated entries)

### 0.1.2
- Changed name to more accurate "HTTP Switchboard"

### 0.1
- First version. Rather bare.