### 0.3.2
- New extension page: "Settings"
- Cookies can optionally be deleted once accounted
- Better cookie reporting in the matrix
- Fixed <https://github.com/gorhill/httpswitchboard/issues/12>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/9>
- Found and fixed a one-time memory leak
- Fixed `localhost` ending up in read-only blacklist
- Blacklisted domains added to project's own list (see [file](/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt) for why):
    * adgear.com
    * bounceexchange.com

### 0.3.1
- Added handling cookies using [`binaryValue`](http://developer.chrome.com/extensions/webRequest.html#type-HttpHeaders) (Not handling cookies using `binaryValue` was preventing the blocking of cookies on the pages where these cookies occurred).
- If an external blacklist can't be obtained, use locally cached copy, if any, so that user is not left naked.
- Latest version of HTTP Switchboard blacklist is always used (as opposed to external blacklists which are cached locally for a week).
- Added more blacklisted domains to [HTTP Switchboard blacklist](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt).
- Added button in popup menu to revert all temporary changes to the whitelist/blacklist (thus no need to reboot chromium/chrome to reset all fiddling with black and whitelist).

### 0.3.0
- A bit of work on [documentation](https://github.com/gorhill/httpswitchboard/wiki/Quick-tour), more to come.
- Added a [project-maintained blacklist](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt), for those domain names which I believe should be blacklisted but are
not found in other blacklists.
- The menu is organized in four logical groups:
    - First, all the requests directly related to the current page,
    - Second, all the whitelisted domains,
    - Third, all the graylisted domains,
    - Fourth, all the blacklisted domains.
- Major change in behavior: Any change to a cell status in the matrix is **temporary** by default, which means the blacklist/whitelist status of a cell will revert to being graylisted when chromium is rebooted. This encourage users to fiddle without worry with the permissions on the page. The user will have to make an extra click (on the padlock) to permanently blacklist/whitelist a cell. I will soon add a button to force a reset, and a user-configurable timeout, so that the user doesn't not have to reboot chromium.
- Now using [URI.js](http://medialize.github.io/URI.js/) thus gaining sensible management of second-level domain names and increasing performance overall.
- Work on performance and reduced memory usage.
- Better default blacklist filters when first installing ("plugin" and "frame" are now blacklisted by default, so that if user toggle master switch to whitelist "all", these types of items will still be effectively blacklisted.)
- In matrix, "object" is renamed "plugin".
- Plugins are now outright blocked if effectively blacklisted (in addition of being prevented from making web requests.)

### 0.2.5
- Fixed bug introduced in 0.2.4 which broke the fetching of remote blacklists.
- IP addresses can now be properly handled.

### 0.2.4
- Show details of remote blacklists being used on info page.
- Ability to filter stats per web page on info page.
- Fixed a bug which caused HTTP Switchboard to diagnose there was actual inline scripting on all pages, regardless whether it was really the case.

### 0.2.3
- Added button in popup menu to easily access info page.
- More work on info page.
- Fix to address the issue of msn.com disregarding standards (as per RFC1738, '|' must be escaped in a URL, msn.com does not escape '|'... culprit URL found at `http://money.ca.msn.com/`).
- Fixed memory leak (something to investigate: non visible web pages can still run their JS in chromium?!)

### 0.2.2
- Remote blacklists will be reloaded from remote servers every 7 days.
- Started work on options page.
- Fixed [issue #1](https://github.com/gorhill/httpswitchboard/issues/1).
- <s>Fixed a memory leak</s>.

### 0.2.1
- More accurate cookie reporting.
- Further fine tuning the UI of the popup menu.

### 0.2.0
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
    * [Peter Lowe's blacklist](http://pgl.yoyo.org/as/index.php): [Ad server hostnames for blocking ads](http://pgl.yoyo.org/as/serverlist.php?mimetype=plaintext) (2,547 entries)
    * [Malware Domain List](http://www.malwaredomainlist.com/): [MalwareDomainList.com Hosts List](http://www.malwaredomainlist.com/hostslist/hosts.txt) (1,651 entries)
- Trivial GUI improvements
- User-defined lists stored format now more similar to third party lists (newline-separated entries)

### 0.1.2
- Changed name to more accurate "HTTP Switchboard"

### 0.1
- First version. Rather bare.