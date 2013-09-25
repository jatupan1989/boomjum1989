### 0.2.00
- Added ability to whitelist/blacklist cookies.
- Added [justdomains](http://dns-bh.sagadc.org/justdomains) blacklist from [DNS-BH – Malware Domain Blocklist](http://www.malwaredomains.com/?page_id=1508) (22,850 entries)
- Ignore fragment in URL when creating/looking URL stats store.

### 0.1.9
- Extension now loads properly when tabs are already present, and when chromium is launched first time
- Better display of web requests count in extension icon when count > 999

### 0.1.8
- Opened popup menu now updates in real-time as net traffic is processed
- Fine tuning visuals

### 0.1.7
- Smart reloading of tabs when extension popup menu closed (only if necessary)
- Improved responsiveness:
    * async update of extension badge
    * caching top url stats for a while, this reduce mem alloc during stats collection
- Fixed an issue with &lt;noscript&gt; tags caused by a bug in Chromium (see <https://code.google.com/p/chromium/issues/detail?id=232410>)
- Fixed code related to some error messages at the console (valid web requests not necessarily matched to a tab, like when the page is pre-rendered -- example: googling for 'wikipedia', wikipedia.org is pre-fetched internally)

### 0.1.6
- Now block inline script tags on top frame when scripts are blacklisted for this top frame (before, only separate script files where prevented from being loaded/executed). Still need to look into this for subframes.
- Added [immortal_domains](http://dns-bh.sagadc.org/immortal_domains.txt) blacklist from [DNS-BH – Malware Domain Blocklist](http://www.malwaredomains.com/?page_id=1508) (2,306 entries)

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
    * [Peter Lowe's blacklist](http://pgl.yoyo.org/as/index.php): [Ad server hostnames for blocking ads](http://pgl.yoyo.org/as/serverlist.php?mimetype=plaintext") (2,547 entries)
    * [Malware Domain List](http://www.malwaredomainlist.com/): [MalwareDomainList.com Hosts List](http://www.malwaredomainlist.com/hostslist/hosts.txt) (1,651 entries)
- Trivial GUI improvements
- User-defined lists stored format now more similar to third party lists (newline-separated entries)

### 0.1.2
- Changed name to more accurate "HTTP Switchboard"

### 0.1
- First version. Rather bare.