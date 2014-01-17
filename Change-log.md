For conciseness, *HTTP Switchboard* is referred as HTTPSB in the text below. This page is often updated **before** the latest version is released.

### 0.7.7.0

- URL redirections are now reported in the matrix of the landing page.
    * URL redirections are recognizabled by a group of domain/subdomains in the matrix for which all the cells are empty. More: [URL redirections]()https://github.com/gorhill/httpswitchboard/wiki/URL-redirections).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/148>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/112>

***

### 0.7.6.1

- Fixed <https://github.com/gorhill/httpswitchboard/issues/145>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/141>.

***

### 0.7.6.0

- **New feature**: Auto-create temporary site-level scope (disabled by default, enable from *Settings* page)
    * When a user creates a site-level scope, he effectively sandboxes the whitelist/blacklist rules to apply only to web pages matching that scope.
    * Example of how this feature works (assuming out of the box settings):
        - User visits <http://arstechnica.com/security/2014/01/more-researchers-join-rsa-conference-boycott-to-protest-10-million-nsa-deal>.
        - **Temporary site-level scope `http://arstechnica.com` automatically created**.
        - Just for demonstration purpose, let's say you are in a hurry so you whitelist "all" (top-left cell) in order to be able to post a comment without having to hunt which specific rules are needed (you will take the time to do so later):
            * This very permissive (temporary) rule would make security conscious users uneasy, however, in this case it applies **only** to web pages which URL address starts with `http://arstechnica.com`.
    * Another virtuous side-effect of sandboxing ruleset using site-level scopes (or to a lesser extent domain-level scopes) is to minimize the spurious reloading of other pages when you change rules for one page. Example:
        - Whitelist `twitter.com` in one page in global scope.
        - Many other pages reload because they were also requesting resources from `twitter.com` (a typically ubiquitous hostname from which resources are pulled from countless web pages).
        - If you sandbox the rules to only one web site, adding or removing rules will only affect web pages of the same web site.
    * Therefore, auto-creating temporary scope for every page you visit enhance security and convenience (this enhances security as long as you don't start to whitelist "all" on *every* web page you visit...)
    * Keep in mind the site-level scope created is **temporary**, unless you persist it (padlock).
        - Currently planning a future option to flush *temporary* scopes and rules after *x* minutes of being unused, in order to avoid runtime bloat of temporary scopes/rules.
    * Turning on the auto-creation of site-level scopes is pointless if you use HTTPSB in an allow-all/block-exceptionally mode.
- **Feature change**: The "Process behind-the-scene HTTP requests" checkbox in the *Settings* page is gone:
    * Users will now have to use the matrix to tell HTTPSB how to filter behind-the-scene requests ("BtSR").
    * For first time installations, the BtSR matrix is in allow-all mode.
    * For existing installations, if "Process behind-the-scene HTTP requests" was...
        - Not checked: BtSR matrix is set to allow-all mode.
        - Checked: BtSR matrix is set to block-all mode.
        - However, HTTPSB will leave the BtSR matrix unchanged if it concludes the user has fiddled with it.
- The behind-the-scene matrix can now be accessed from any of HTTPSB web pages, not just the *Statistics* page.
- Added another third-party list of blocked hosts: <http://winhelp2002.mvps.org/hosts.txt> (turned off by default).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/137>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/126>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/124>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/119>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/105>:
    * The fix is to copy whatever rules from global (and possibly domain-level) scope which is relevant to the newly created scope. Here is the logic of the copy-rules algorithm:
        - Copy whitelist rules **only** if they are relevant to the web page for which a scope is newly created.
        - Copy all blacklist and graylist rules.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/73>

***

### 0.7.5.0
- **New feature**: Ability to use the matrix on behind-the-scene requests ([issue #122](/gorhill/httpswitchboard/issues/122)).
    * Since the matrix reflects the network traffic of a web page, in order to access the matrix for behind-the-scene requests I had to pick a web page to allow for this.
    * The web page picked is the *Statistics* page. So if you go to the *Statistics* page, HTTPSB's popup menu will show the matrix populated according to behind-the-scene requests.
    * A default scope called `http://chromium-behind-the-scene` is created by default for behind-the-scene rules.
    * **Important read to prevent any misunderstanding**: [Behind-the-scene requests](https://github.com/gorhill/httpswitchboard/wiki/Behind-the-scene-requests)
    * Remember, whitelist/blacklist rules in the matrix for behind-the-scene requests will apply **only** if the option "Process behind-the-scene HTTP requests" is enabled on the *Settings* page.

***

### 0.7.4.2
- More work done on translation by volunteers:
    * Deutsch ([issue #123](/gorhill/httpswitchboard/issues/123)) von [tlu1024](https://github.com/tlu1024)
    * Français ([issue #69](/gorhill/httpswitchboard/issues/69)) par [tailHey](https://github.com/tailHey)
- **"Plugin"** column in the matrix is no longer blacklisted by default for first install.
    * **It is strongly recommended** that new users enable "Click to play" for plugins in their Chromium-based browser settings.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/125>

***

### 0.7.4.1
- German translation ongoing, thanks to [tlu1024](https://github.com/tlu1024):
    * <https://github.com/gorhill/httpswitchboard/issues/123>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/116>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/110>
- All third-party blacklists have been updated to their latest version.
    * Note that `assets/thirdparties/hosts-file.net/hosts.txt` [has grown from ~240,000 to ~350,000](http://hphosts.blogspot.ca/2014/01/hphosts-updated-04012014.html) (this list is not enabled out of the box, but if you enabled it, expect more memory consumed by HTTPSB with this latest version).
    * Note that 9,290 hostnames [were delisted](http://www.malwaredomains.com/?p=3504) from `assets/thirdparties/mirror1.malwaredomains.com/files/justdomains`. This will save memory in HTTPSB.
    * For further details of what changed in the preset blacklists, [see the diffs](/gorhill/httpswitchboard/commit/1e870fdc646aaa01b93579fa160a88497138abfd).

***

### 0.7.4.0
- **New setting**: "Clear browser cache every [x] minutes."
    * This is to take care of those trackers which use browser cache tricks to track you:
        - [Preventing Web Tracking via the Browser Cache](https://grepular.com/Preventing_Web_Tracking_via_the_Browser_Cache)
        - [Cookieless cookies](http://lucb1e.com/rp/cookielesscookies/)
    * To implement this feature a new permission is required: ["browsingData"](http://developer.chrome.com/extensions/browsingData.html).
    * Since a new permission is required, I believe your browser might ask you to confirm the updating of the extension.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/97>

***

### 0.7.3.1
- Fixed <https://github.com/gorhill/httpswitchboard/issues/111>
    * Slight change in behavior of drop down menus in extension popup.

***

### 0.7.3.0
- **New privacy option**: In *Settings* page, "Remove third-party HTTP referer information for non-whitelisted hostname".
    * The [HTTP referer](https://en.wikipedia.org/wiki/HTTP_referer) is a potential threat to privacy. This option allows to have the HTTP referer header removed when these two conditions are met:
        - The domain name of the referer is different than the domain name of the request.
        - The hostname of the request is not whitelisted.
    * For example, let's say:
        - `www.foo.com` requests an image from `images.bar.com`
            * If `bar.com` is not whitelisted, the referer information is removed
            * If `bar.com` is whitelisted, the referer information is NOT removed
        - `www.foo.com` requests an image from `images.foo.com`
            * the referer information is NOT removed
- The list of preset blacklists has been moved from the *Statistics* page to the *Settings* page.
    * Because really, these are settings.
- Two new counters added to the *Statistics* page (in order to make you feel good about using *HTTP Switchboard*):
    * Number of foiled [HTTP cookie](https://en.wikipedia.org/wiki/HTTP_cookie) headers
    * Number of foiled [HTTP referer](https://en.wikipedia.org/wiki/HTTP_referer) headers

***

### 0.7.2.0
- Completed the Rule manager. Three new buttons at the top:
    * "Commit All":
        - All temporary scopes and rules will become permanent.
        - All scopes and rules marked for deletion will be deleted.
    * "Revert All":
        - All temporary scopes and rules will be removed.
        - All scopes and rules marked for deletion will be unmarked.
    - "Remove All":
        - All scopes and rules will be deleted (you must confirm).
    - To mark a scope or rule for deletion, click on the item.
    - As before, you can import/export rules.
- Regarding <https://github.com/gorhill/httpswitchboard/issues/104>: I can't fully test the problem there as this requires OSX, and I have no access to a Mac. Any assistance in debugging on OSX is welcomed. I did take care of a problem on Windows-based Yandex browser though, whereas the layout of the toolbar at the top was broken, resulting in the extension becoming rather unusable.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/103>
    * Got rid of Bootstrap dependency.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/102>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/101>

***

### 0.7.1.2
- Fixed <https://github.com/gorhill/httpswitchboard/issues/98>

***

### 0.7.1.1
- Updated third-party preset blacklists to their latest version.
- Made [Dan Pollock's blacklist](http://someonewhocares.org/hosts/) active by default for a new install (it was off by default).
    * It's a high quality blacklist, carefully maintained, it deserves to be used out of the box.

***

### 0.7.1.0
- **Important**: UI change:
    * ![UI changes](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/v0.7.1.0-screenshot-2.png)
- Locking down the status of a matrix cell:
    * The padlock icons used to lock down a cell status are gone.
    * You can lock down the status of all cells in the matrix using the single padlock button at the top.
    * Using the single padlock button at the top won't affect temporary rules which are not currently displayed in the matrix. Only the rules which are present in the current matrix will be locked down.
- Better scoping, now three scope levels:
    * Global: no change, as before.
    * Domain: new. Example: `https://*.google.com`.
        - This will take care of a lot of pain when creating rules for those domain names which offer many various services. Best example is `google.com`. I don't want to be tracked by `google.com` (not whitelisted globally), but I do want `google.com` and associated subdomains to be whitelisted when visiting one of its subdomains.
        - Creating a per-site ruleset for `https://plus.google.com`, `https://support.google.com`, `https://translate.google.com`, etc. was a real burden.
        - Now I can create one per-domain ruleset, `https://*.google.com`, to take care of all the previous per-site rulesets.
    * Site: no change, as before. Example: `https://plus.google.com`.
    * Scoping is now temporary by default. Use top padlock button to make it permanent.
        - This opens the door to this interesting feature: Auto site-scope temporarily ([request from a user](https://github.com/gorhill/httpswitchboard/issues/43#issuecomment-29162723), thought it was a good idea). Will see if I include this in this release.
    * Scope lookup at request eval time is now smarter: Example: If visiting `https://facebook.com`, per-site ruleset `http://facebook.com` will be used if it exists. However, the reverse is not true.
- **New feature**: Auto-whitelisting of the domain of the visited web page. Default is off. Go to <i>Settings...</i> page to turn it on.
    * I personally advise against, but some people really want it. So be it.
    * A reminder: blocking `frame` by default prevent [that kind of problem](http://arstechnica.com/security/2013/10/hackers-compromise-official-php-website-infect-visitors-with-malware/).
- Smarter smart reload:
    * Blocking formerly unblocked requests won't result in a page reload, *except* for scripts (because they need to be disabled).
    * So for example, if I block previously unblocked images, there is no need to reload the page, as the already loaded images are not affecting the page's behavior, just its look.
- Page can be force-reloaded from the popup menu.
    * This means you can now apply and see the result of your changes without having to close the popup menu.
- Now using [Font Awesome](http://fontawesome.io/) instead of PNG icons wherever possible.
    * This simplifies styling a lot: size, colour, etc. through CSS.
- Fixed:
    * <https://github.com/gorhill/httpswitchboard/issues/96>
    * <https://github.com/gorhill/httpswitchboard/issues/95>
    * <https://github.com/gorhill/httpswitchboard/issues/94>
    * <https://github.com/gorhill/httpswitchboard/issues/90>
    * <https://github.com/gorhill/httpswitchboard/issues/23>

***

### 0.7.0.0
- **Important**: UI change (as per [issue #87](/gorhill/httpswitchboard/issues/87)):
    * A new column has been added in the matrix: "css", which acts on/reports:
        - Stylesheets
        - Web fonts (these are no longer reported in the "other" column)
    * Adding a new column required that I revisited the visuals of the matrix, due to limited horizontal space.
        - Especially, the visual for the "permanent" status of a cell has changed in order to take up less horizontal space. It is somewhat more subtle, but we get used to it. (Spent hours trying to figure the best visual, and nothing else I tried worked IMO.)
    * Result is that now important stylesheet requests are no longer buried in the obscure "other" column.
        - I decided to also report web fonts in the "css" column, as these contribute, just like stylesheets, to the appearance of web pages.
    * The "css" column will default to being whitelisted (just like images).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/91>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/87>

***

### 0.6.9.0
- Overhaul of cookie management code = robustness and performance enhancement.
- New user setting: "[ ] Delete non-blocked session cookies [?] minutes after last time they have been used."
    * [Because W3C](http://www.w3.org/2001/tag/2010/09/ClientSideStorage.html): "A session cookie ... is erased when you end the browser session", except that in Chromium, this is [not happening](https://code.google.com/p/chromium/issues/detail?id=128513). This setting lets you make it happening.
    * FYI, session cookies are typically used to keep users logged in into a web site. So long as a session cookie still exists and is valid from the web site's point of view, you are still logged in.
- Cookie janitor code is back: this gets rid of any unused cookies from non-whitelisted hostnames which might be present in your browser.
    * Be aware that some extensions use cookies which are created from hostnames which might not have been whitelisted.
        - For example, LastPass needs cookies from `lastpass.com`, so be sure to whitelist cookies for `lastpass.com` (by visiting LastPass web site, so that you can use HTTPSB matrix).
    * There is no way for the cookie janitor to know whether a stale cookie was created by an extension or a web page, so if an extension misbehave, it could be because of cookies being deleted under its feet (all cookie managers will potentially interfere, this is not specific to HTTPSB). The fix is to identify and whitelist the hostname of the cookie, or to disable the "Delete blocked cookies" option.
    * The cookie janitor is easy going though, only non-whitelisted orphan cookies which have been stale for more than two hours will be removed.
- Added tooltip for "other" header in the matrix to help people remember what is in this column.
- New entries in context menu to quickly access "Rule manager", "Statistics", and "Settings" pages.
- Improved navigation to extension pages: tab will become active if it is being reused (wasn't working before).
- Third-party blacklists have been updated to their latest version.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/79>
    * For some web site, there will still be a lot of cookie entries in the log in the *Statistics* page: this is because the site changes the value of cookies very often, it's not because HTTPSB over-report.

***

### 0.6.8.1
- Fixed ["Sometimes web page reload after closing popup menu even when no change made"](https://github.com/gorhill/httpswitchboard/issues/85)
    * This one was introduced back in [version 0.6.6](/gorhill/httpswitchboard/wiki/Change-log#066) :-(

***

### 0.6.8.0
- Third-party blacklists can now be selectively enabled/disabled (from the *Statistics* page).
    * So now you are free to browse the web naked if it is your thing.
- Number of distinct entries in each third-party blacklist is now shown in the *Statistics* page.
- Added two more third-party blacklists (from now on, *newly* added third-party blacklists will always be disabled by default):
    * hosts-file.net/hosts.txt (huge!) (from [hpHosts online](http://hosts-file.net/?s=Download))
    * someonewhocares.org/hosts/hosts (from [Dan Pollock](http://someonewhocares.org/hosts/))
        - Suggested by [this pull requester](/ics-forks/httpswitchboard/commit/87e88e86c502cb506626a21752c58deec9989067) (I merged manually)
- While at it, simplified/cleaned up/improved legacy code from when third-party blacklists were downloaded from their remote location (which was not a polite thing to do).
- New version/revision scheme: a fourth number is now used to denote when third party resources have been updated or when regression bugs are fixed.
- Small fixes in blacklist names to ensure a click on a blacklist link will result in the blacklist being loaded in the browser, so that you can see its content.
- Merged pull request <https://github.com/gorhill/httpswitchboard/pull/84>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/78>

***

### 0.6.7
-  No change for existing users. First time HTTPSB is installed, requests of type "other" are whitelisted by default. This is the best option given the last update in which stylesheets are treated as 'other' for 3rd-party hostnames. Even without this change in version 0.6.6, I had been leaning toward whitelisting by default the "other" column because it is often used also for [web fonts](/gorhill/httpswitchboard/wiki/FAQ#in-the-top-left-of-the-matrix-what-is-other).

***

### 0.6.6
- Fixed <https://github.com/gorhill/httpswitchboard/issues/76>.
    * **IMPORTANT:** stylesheets (`.css` files) which are pulled from hostnames which do not match the domain name of the top web page will be reported as "other" in the pop-up menu matrix.
        - I realize many web pages which were displaying properly before this last update might now not display properly, but the reason they were displaying properly before is because requests (stylesheet) on which you had no control were made. Now you have full control.
        - Remember: if a web page doesn't display properly, it might be because the requests for stylesheets are blocked. Requests for stylesheet are counted in the "other" column. Example, three stylesheets at `cbsistatic.com`:
        - ![Three stylesheets shown in "other" @ "cbsistatic.com"](https://raw.github.com/gorhill/httpswitchboard/master/doc/img/matrix-other-column.png)
        - Remember: with this update, you are now in control of your privacy: you choose where your browser is allowed to connect.

***

### 0.6.5
- Fix required in order to be able to run as an Opera add-on.
    * In Opera, `onBeforeRequest` can be called before the URL is bound to tab, thus preventing the blocking of inline javascript.
    * Maybe the above problem also affected Chromium/Chrome, so I pushed the new version to Chrome web store as well.
    * The fix is: if HTTPSB is unable to evaluate **with 100% certainty** whether javascript should be enabled, javascript **will not** be enabled.
    * Extension has been submitted to Opera add-on collection, ~~it might take a few days before it shows up~~ never mind, it was rejected, I figured the Chromium screenshots might cause an issue. Opera users can still [install the extension manually](/gorhill/httpswitchboard/tree/master/dist#install) though.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/74>

***

### 0.6.4
- Fixed <https://github.com/gorhill/httpswitchboard/issues/35> -- Read carefully:
    * HTTPSB no longer uses Chrome/Chromium settings to block inline javascript, because the way Chromium/Chrome's javascript blocker works is incompatible with how HTTPSB works. This means:
        - You won't see Chromium/Chrome's "javascript blocked" icon in the omnibar (**do not panic**).
        - Here are some links where you can test whether HTTPSB blocks javascript if you doubt: <https://github.com/gorhill/httpswitchboard/issues/46>.
        - On the positive side, you don't have to care about the initial Chromium/Chrome settings regarding javascript (so no more "IMPORTANT NOTE!" required).
    * How it works (for the technically inclined):
        - At startup time, HTTPSB creates two rules in Chromium/Chrome to allow javascript from everywhere (**do not panic**).
        - Then when the user opens a web page where inline javascript must be blocked, the following directive is added to the incoming response headers: `Content-Security-Policy: script-src 'none'`. This prevents inline javascript from running on the main page. (More details regarding [Content Security Policy](http://www.html5rocks.com/en/tutorials/security/content-security-policy/)).
        - For external javascript, this is taken care as it always has been since the beginning, by cancelling the requests to fetch the external resource.

***

### 0.6.3
- Context menu entries:
    * To temporarily whitelist all for domain of ***current page***
    * To revert temporary permissions

***

### 0.6.2
- Support for [Internationalized Domain Name](http://en.wikipedia.org/wiki/Internationalized_domain_name) through [punycode.js](https://github.com/bestiejs/punycode.js). Examples:
    * <http://xn--u9jxb009mixgdp9b.jp/>
    * <http://xn--rksmrgs-5wao1o.josefsson.org/>
    * <http://www.xn--kpabt-pra9i.eu/>
- Support for complete [Public Suffix List](http://publicsuffix.org/) ("PSL") through [publicsuffixlist.js](https://github.com/gorhill/publicsuffixlist.js) to determine the domain of a specific hostname. Examples:
    * `googleblog.blogspot.ca` is now reported as a domain (prior to v0.6.2, `blogspot.ca` was deemed the domain);   
    * `twitter.github.io` is now reported as a domain (prior to v0.6.2, `github.io` was deemed the domain);
    * `kpbsd.k12.ak.us` is now reported as a domain (prior to v0.6.2, `ak.us` was deemed the domain);
    * Etc.
- Master power switch to completely disengage blocking of everything (beware!), so you don't have to uninstall HTTP Switchboard if for some reasons you don't want to filter anything temporarily (HTTPSB will still continue to log HTTP requests though, so at least you can see what you subject yourself to without a blocker.)
- Ability to adjust the size of the log buffer. Can be set to `0` to reduce memory usage if you have no interest whatsoever in examining details of HTTP traffic.
- Display filters of logged HTTP traffic in the *Statistics* page are now persisted.
- Version française entamée.
- Added to HTTPSB's blacklist:
    * `analytics.edgesuite.net`
    * `atedra.com`
    * `clicktale.net`
    * `everestjs.net`
    * `everesttech.net`
- Fixed:
    * <https://github.com/gorhill/httpswitchboard/issues/54>
    * <https://github.com/gorhill/httpswitchboard/issues/49>
    * <https://github.com/gorhill/httpswitchboard/issues/36>
    * <https://github.com/gorhill/httpswitchboard/issues/28>

***

### 0.6.1
- Further fix to <https://github.com/gorhill/httpswitchboard/issues/55>:
    * Be less strict for when a subdomain can be collapsed:
        - Before: No subdomain could be collapsed if it, or one peer subdomain had at least one explicit block/allow rule in one if its columns.
        - Now: Only a subdomain which has at least one explicit block/allow rule in one of its columns can't be collapsed. Other rule-less peer subdomains are now collapsible.

***

### 0.6.0
- Fixed <https://github.com/gorhill/httpswitchboard/issues/67>.
- New blacklisted entry:
    * `clicktale.com`: "See absolutely everything your visitors do on your webpage ... See their every mouse move, click and keystroke"

***

### 0.5.9
- Fixed <https://github.com/gorhill/httpswitchboard/issues/61>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/55>.
- [Updated](/gorhill/httpswitchboard/commit/8a5af0c5558e357cb0f52f819f0d6eb66a0ae442) third-party blacklists to latest versions.
- More work internally to support internationalization.

***

### 0.5.8
- Fixed <https://github.com/gorhill/httpswitchboard/issues/60>.
- Some groundwork to support internationalization (volunteer translators are welcomed).

***

### 0.5.7
- Fixed <https://github.com/gorhill/httpswitchboard/issues/56>.

***

### 0.5.6
- New feature: *Rule manager*.
    * Backup in part or whole your rules.
    * Restore in part or whole your rules.
    * Exchange "recipes" with others.
        - Example: [Youtube, with comments enabled](https://groups.google.com/d/msg/httpsb/hys6JtTGwD8/61HlKY4NlbwJ).
        - The idea is to make it easy for the geekier to help less geeky people use the absolute minimal set of rules required to make a web page/site work correctly, so that having to whitelist all can be avoided.
    * Consider this new feature early beta, more details to add (delete rules, scopes, etc.) or think through.
- Reorganized pop-up menu layout to allow for new features without cluttering the UI.
- Imported contributions from [GuardianMajor](/GuardianMajor) to make *Settings* page slicker.
    * Originally presented as a [pull request](/gorhill/httpswitchboard/pull/57) (I merged manually)

- Imported latest version of [third-party blacklists](/gorhill/httpswitchboard/tree/master/assets/thirdparties).

***

### 0.5.5
- Fixed <https://github.com/gorhill/httpswitchboard/issues/53>.

***

### 0.5.4
- Fixed <https://github.com/gorhill/httpswitchboard/issues/51>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/50>.

***

### 0.5.3
- *Settings*: user can now choose size of text in matrix (as [suggested by a user](/gorhill/httpswitchboard/issues/44)).
- *Popup menu*: Blacklisted hostnames section can be collapsed/expanded.
- New Google groups to informally discuss HTTP Switchboard: <https://groups.google.com/forum/?hl=en#!forum/httpsb>.

***

### 0.5.2
- Fixed <https://github.com/gorhill/httpswitchboard/issues/42>

***

### 0.5.1
- Implemented ability to have [local storage](http://en.wikipedia.org/wiki/Web_storage) wiped out for hostnames which have *cookies* blacklisted (see *Settings* page).
- More [blacklisted hostnames](/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt):
    * erovinmo.com

***

### 0.5.0
- New feature: [per-site permissions](https://github.com/gorhill/httpswitchboard/wiki/Per-site-permissions:-an-example). For example, this allows:
    * Blacklist hostname `facebook.com` globally,
    * Whitelist hostname `facebook.com` when visiting `https://www.facebook.com`.
    * Net result: this disables `facebook.com` from tracking you (like when you visit a web site in which `facebook.com` has assets embedded), except when visiting a web page on `https://www.facebook.com`.
- Extension icon offers a sense of how much is allowed/blocked on the page.
- Users have now the ability to permanently override the blacklist status of read-only blacklisted entries.
- Added another third-party blacklist: [ad_servers.asp](http://hosts-file.net/ad_servers.asp) from <http://hosts-file.net/>. (So expect more dark red cells at the bottom of the matrix).
- Updated other third-party blacklists to their latest version.

***

### 0.4.0
- Fixed <https://github.com/gorhill/httpswitchboard/issues/33>.

***

### 0.3.9
- Fixed <https://github.com/gorhill/httpswitchboard/issues/31>.

***

### 0.3.8
- Added a switch in the *Settings* page to let the user choose whether to use [**strict blocking**](/gorhill/httpswitchboard/wiki/%22Strict-blocking%22-illustrated) (introduced in 0.3.6) or not. Default is `off`. If you like this feature, be sure to turn it on.

***

### 0.3.7
- Fixed <https://github.com/gorhill/httpswitchboard/issues/30>.

***

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

***

### 0.3.5
- Further reduction of memory footprint and further performance improvement.

***

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

***

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

***

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

***

### 0.3.1
- Added handling cookies using [`binaryValue`](http://developer.chrome.com/extensions/webRequest.html#type-HttpHeaders) (Not handling cookies using `binaryValue` was preventing the blocking of cookies on the pages where these cookies occurred).
- If an external blacklist can't be obtained, use locally cached copy, if any, so that user is not left naked.
- Latest version of HTTP Switchboard blacklist is always used (as opposed to external blacklists which are cached locally for a week).
- Added more blacklisted hostnames to [HTTP Switchboard blacklist](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb-blacklist.txt).
- Added button in popup menu to revert all temporary changes to the whitelist/blacklist (thus no need to reboot chromium/chrome to reset all fiddling with black and whitelist).

***

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

***

### 0.2.5
- Fixed bug introduced in 0.2.4 which broke the fetching of remote blacklists.
- IP addresses can now be properly handled.

***

### 0.2.4
- Show details of remote blacklists being used on info page.
- Ability to filter stats per web page on info page.
- Fixed a bug which caused HTTP Switchboard to diagnose there was actual inline scripting on all pages, regardless whether it was really the case.

***

### 0.2.3
- Added button in popup menu to easily access info page.
- More work on info page.
- Fix to address the issue of msn.com disregarding standards (as per RFC1738, '|' must be escaped in a URL, msn.com does not escape '|'... culprit URL found at `http://money.ca.msn.com/`).
- Fixed memory leak (something to investigate: non visible web pages can still run their JS in chromium?!)

***

### 0.2.2
- Remote blacklists will be reloaded from remote servers every 7 days.
- Started work on options page.
- Fixed [issue #1](https://github.com/gorhill/httpswitchboard/issues/1).
- <s>Fixed a memory leak</s>.

***

### 0.2.1
- More accurate cookie reporting.
- Further fine tuning the UI of the popup menu.

***

### 0.2.0
- Added ability to whitelist/blacklist cookies.
- Added [justdomains](http://dns-bh.sagadc.org/justdomains) blacklist from [DNS-BH – Malware Domain Blocklist](http://www.malwaredomains.com/?page_id=1508) (22,850 entries)
- Ignore fragment in URL when creating/looking URL stats store.

***

### 0.1.9
- Extension now loads properly when tabs are already present, and when chromium is launched first time
- Better display of web requests count in extension icon when count > 999

***

### 0.1.8
- Opened popup menu now updates in real-time as net traffic is processed
- Fine tuning visuals

***

### 0.1.7
- Smart reloading of tabs when extension popup menu closed (only if necessary)
- Improved responsiveness:
    * async update of extension badge
    * caching top url stats for a while, this reduce mem alloc during stats collection
- Fixed an issue with &lt;noscript&gt; tags caused by a bug in Chromium (see <https://code.google.com/p/chromium/issues/detail?id=232410>)
- Fixed code related to some error messages at the console (valid web requests not necessarily matched to a tab, like when the page is pre-rendered -- example: googling for 'wikipedia', wikipedia.org is pre-fetched internally)

***

### 0.1.6
- Now block inline script tags on top frame when scripts are blacklisted for this top frame (before, only separate script files where prevented from being loaded/executed). Still need to look into this for subframes.
- Added [immortal_domains](http://dns-bh.sagadc.org/immortal_domains.txt) blacklist from [DNS-BH – Malware Domain Blocklist](http://www.malwaredomains.com/?page_id=1508) (2,306 entries)

***

### 0.1.5
- Added ability to block whole page
- Blocked subframes (&lt;iframe&gt;, etc.) are now redirected to a safe page (so there is a visual to indicate blocking)
- In a new install page & images are whitelisted by default
- Now using <a href="http://www.google.com/fonts/specimen/Roboto+Condensed">Roboto Condensed font</a>, better suited for the matrix
- Reworked project structure and code in order to grow better

***

### 0.1.4
- Fine tuned local storage

***

### 0.1.3
- Using built-in community-built blacklists from:
    * [Peter Lowe's blacklist](http://pgl.yoyo.org/as/index.php): [Ad server hostnames for blocking ads](http://pgl.yoyo.org/as/serverlist.php?mimetype=plaintext) (2,547 entries)
    * [Malware Domain List](http://www.malwaredomainlist.com/): [MalwareDomainList.com Hosts List](http://www.malwaredomainlist.com/hostslist/hosts.txt) (1,651 entries)
- Trivial GUI improvements
- User-defined lists stored format now more similar to third party lists (newline-separated entries)

***

### 0.1.2
- Changed name to more accurate "HTTP Switchboard"

***

### 0.1
- First version. Rather bare.