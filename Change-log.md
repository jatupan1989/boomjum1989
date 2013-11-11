### 0.5.2
- Fixed <https://github.com/gorhill/httpswitchboard/issues/42>

### 0.5.1
- Implemented ability to have [local storage](http://en.wikipedia.org/wiki/Web_storage) wiped out for hostnames which have *cookies* blacklisted (see *Settings* page).
- More [blacklisted hostnames](/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt):
    * erovinmo.com

### 0.5.0
- New feature: per-page permissions. For example, this allows:
    * Blacklist hostname `facebook.com` globally,
    * Whitelist hostname `facebook.com` when visiting `https://www.facebook.com`.
    * Net result: this disables `facebook.com` from tracking you (like when you visit a web site in which `facebook.com` has assets embedded), except when visiting a web page on `https://www.facebook.com`.
- Extension icon offers a sense of how much is allowed/blocked on the page.
- Users have now the ability to permanently override the blacklist status of read-only blacklisted entries.
- Added another third-party blacklist: [ad_servers.asp](http://hosts-file.net/ad_servers.asp) from <http://hosts-file.net/>. (So expect more dark red cells at the bottom of the matrix).
- Updated other third-party blacklists to their latest version.

### 0.4.0
- Fixed <https://github.com/gorhill/httpswitchboard/issues/33>.

### 0.3.9
- Fixed <https://github.com/gorhill/httpswitchboard/issues/31>.

### 0.3.8
- Added a switch in the *Settings* page to let the user choose whether to use [**strict blocking**](/gorhill/httpswitchboard/wiki/What-is-"strict-blocking"%3F) (introduced in 0.3.6) or not. Default is `off`. If you like this feature, be sure to turn it on.

### 0.3.7
- Fixed <https://github.com/gorhill/httpswitchboard/issues/30>.

### 0.3.6
- **Change in behavior, read carefully!**
    * Before 0.3.6:
        - A "gray" matrix cell was whitelisted through sole inheritance from an expressly whitelisted hostname, regardless whether the type of request for this "gray" matrix cell was blacklisted.
    * After 0.3.5, now the rule is more strict:
        - A "gray" matrix cell will be whitelisted through inheritance if and only if **none** of the inherited hostname **and** inherited type of request is expressly blacklisted.
    * Concretely, using [an example](/gorhill/httpswitchboard/wiki/What-is-"strict-blocking"%3F): let's posit *frames* are expressly blacklisted, hostname *arstechnica.net* is expressly whitelisted:
        - Before 0.3.6: *frames* for *arstechnica.net* were whitelisted (through inheritance).
        - After 0.3.5: *frames*  for *arstechnica.net* are blacklisted (through inheritance).
    * In this example, if you really want *frames* for *arstechnica.net* to be whitelisted while keeping the general blacklisting of *frames* (which is good), then you need to expressly and specifically whitelist *frames* for *arstechnica.net*, meaning not relying anymore on inheritance.
    * Why the change? It's common for drive-by malware to inject `<iframe>` in order to activate themselves (example: <http://arstechnica.com/security/2013/10/hackers-compromise-official-php-website-infect-visitors-with-malware/>)
- **Change in behavior, read carefully!**
    * Clicking on a matrix cell doesn't cycle through black, white and graylist anymore:
        - Click in the upper half of a cell, you will toggle between white and graylist.
        - Click in the lower half of a cell, you will toggle between black and graylist.
    * This change addresses what I considered two annoyances:
        - Annoyance #1: You would have to click more than once on a cell to whitelist.
        - Annoyance #2: It was difficult to predict what would happen to the cell once clicked.
- More work toward reducing memory footprint and improving performance.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/22>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/29> (Matrix behavior changed!)

### 0.3.5
- Further reduction of memory footprint and further performance improvement.

### 0.3.4
- New *Chromium-behind-the-scene* virtual tab intercepts net requests made by the browser behind the scene and process these hidden requests against the current whitelist/blacklist. You can look at these requests through the *Global info* page: in the *Geeky stats* section, use the drop-down list to select "http://chromium.behind.the.scene". More information regarding what the browser can send behind the scene is disclosed at [Google Chrome Privacy Whitepaper](http://www.google.com/intl/en/chrome/browser/privacy/whitepaper.html)
- All third parties blacklists are now [available locally](/gorhill/httpswitchboard/tree/master/assets/thirdparties), which brings many advantages:
    * Blacklists are loaded independently of availability of remote sites where they sit.
    * Loading blacklists from remote sites is no longer complicated by the fact the user setting *"Process behind-the-scene requests"* could be switched on.
    * This saves on local storage space.
- Further reduction of memory footprint and further performance improvement.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/27>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/26>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/25>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/24>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/21>.
- More blacklisted hostnames:
    * eyereturn.com: "eyeReturn Marketing is the only end-to-end digital advertising platform in the market"
    * lduhtrp.net
    * yceml.net

### 0.3.3
- Now reporting the number of cookies effectively removed by HTTP Switchboard (see *Settings* pages).
- Further reduced memory footprint and performance improvement.
- Popup menu responsiveness: avoid using slow jQuery.data() if it can be avoided, which was the case here.
- Fixed another memory leak issue (forgot to put planned code to purge internal cacher).
- Fixed the counting of cookies on the *Info* page.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/19>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/18>.
- More blacklisted hostnames:
    * 2mdn.net: "2mdn.net is a domain used by Doubleclick which is an advertising company..."
    * adnxs.com: "Adnxs.com is run by AppNexus, a company that provides technology, data and analytics to help companies buy and sell online display advertising" (Ref.: http://www.theguardian.com/technology/2012/apr/23/adnxs-tracking-trackers-cookies-web-monitoring)
    * adobetag.com: "Adobe Announces Adobe Tag Manager for the Online Marketing Suite"
    * crosspixel.net: "leading provider of high performance audience data and information for the real-time advertising industry"
    * crsspxl.com: Related to crosspixel.net
    * gigya.com: "The tools you need to connect with consumers, harness rich data, and make marketing relevant"
    * mookie1.com: "Specializing in online digital advertising, search marketing"
    * servebom.com: no home page, seen as 'tracking.servebom.com': good enough for this list

### 0.3.2
- New extension page: "Settings".
- Cookies can optionally be deleted once accounted for.
- Better cookie reporting in the matrix.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/12>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/9>.
- Found and fixed a one-time memory leak.
- Fixed `localhost` ending up in read-only blacklist.
- Blacklisted hostnames added to project's own list:
    * adgear.com: "AdGear is an online advertising technologies company"
    * bounceexchange.com: "The BounceX software is tracking all the cursor movements of every visitor in real-time"

### 0.3.1
- Added handling cookies using [`binaryValue`](http://developer.chrome.com/extensions/webRequest.html#type-HttpHeaders) (Not handling cookies using `binaryValue` was preventing the blocking of cookies on the pages where these cookies occurred).
- If an external blacklist can't be obtained, use locally cached copy, if any, so that user is not left naked.
- Latest version of HTTP Switchboard blacklist is always used (as opposed to external blacklists which are cached locally for a week).
- Added more blacklisted hostnames to [HTTP Switchboard blacklist](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt).
- Added button in popup menu to revert all temporary changes to the whitelist/blacklist (thus no need to reboot chromium/chrome to reset all fiddling with black and whitelist).

### 0.3.0
- A bit of work on [documentation](https://github.com/gorhill/httpswitchboard/wiki/Quick-tour), more to come.
- Added a [project-maintained blacklist](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt), for those domain names which I believe should be blacklisted but are
not found in other blacklists.
- The menu is organized in four logical groups:
    - First, all the requests directly related to the current page,
    - Second, all the whitelisted hostnames,
    - Third, all the graylisted hostnames,
    - Fourth, all the blacklisted hostnames.
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