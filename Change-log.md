For conciseness, *HTTP Switchboard* is referred as HTTPSB in the text below. This page is often updated **before** the latest version is released.

**IMPORTANT:** [Compatibility with various Chromium based browsers and other extensions](/gorhill/httpswitchboard/wiki/Compatibility-with-various-Chromium-based-browsers-and-other-extensions)


***

### 1.0.0.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_1.0.0.1.zip) date: 5 July 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/366>: "Blocked sites no longer have an entry in the matrix".
    - Bug was introduced [on June 29](/gorhill/httpswitchboard/commit/62202fd87f90061359ba5a7272b6f9f06095e107) just by reformatting the code...

***

### 1.0.0.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_1.0.0.0.zip) date: 5 July 2014
- **New setting**: "Copy all rules from global scope into newly created local scopes"
    - Because of [issue #349](/gorhill/httpswitchboard/issues/349) and a handful of others I had closed as "won't fix".
    - Disabled by default. When disabled, HTTPSB behaves just like before.
    - It is mostly useful if you make heavy use of scopes (I do), for instance, if you enabled the auto-creation of scopes.
    - The copying occurs **only** at scope creation time, so if you add rules in the global scope *after* the local scope is created, these won't be copied.
    - If you have a global scope with a lots of rules, this means all the these will be copied in newly created local scopes. Mind the potential rule bloat (_Scoped rules_ manager will be handy here).
    - Hence this feature is really only suited for those who work **only** with scopes, and in such case the global scope would be only used to create fine-grained rules which the user wishes to apply everywhere automatically.
- The privacy-related settings have moved from the _Settings_ tab into a new _Privacy_ tab.
- Translation work by many [contributors](/gorhill/httpswitchboard/graphs/contributors).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/364>: "Sign in to Chrome" crashes the browser".
    - A scope is automatically created for `chrome-scheme` and its `all` cell is whitelisted. If you already have an existing scope for `chrome-scheme`, it will replace the default one.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/361>: "EasyList Czech and Slovak moved".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/360>: "Some ads are not blocked".
    - I couldn't see the ads on my side, so hopefully this will be fixed, I will await feedback.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/353>: "Improved message text for 'ubiquitousFormatHint' and 'ubiquitousAllowFormatHint'".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/352>: "Show frame source over blocked frames".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/349>: "When using (auto create) domain level scope, how do I create a rule that auto aplies to each scope when it is created?".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/194>: "Move the Settings tab's Privacy section to its own tab".

***

### 0.9.9.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.9.1.zip) date: 21 June 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/344>: "UA-spoofing disregards user-chosen UA strings for first cycle".

***

### 0.9.9.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.9.0.zip) date: 20 June 2014
- **New privacy setting**: _"Block all hyperlink auditing attempts"_
    * See ["On-privacy: hyperlink auditing"](/gorhill/httpswitchboard/wiki/On-privacy#hyperlink-auditing).
    * Enabled by default: hyperlink-auditing is purely for tracking purpose, there is no benefit to the user.
- Translation work by [various contributors](/gorhill/httpswitchboard/graphs/contributors).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/345>: "Avoid using `chrome.runtime.sendMessage()` wherever possible".
    * I suspect using `chrome.runtime.sendMessage()` was causing a trickle of memory leaks which overtime pushed up the baseline memory footprint of HTTPSB.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/343>: "Please add datarating.com to blacklist.txt".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/342>: "Address _Hyperlink auditing_".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/302>: "Google Drive (spreadsheet) Issue" via fix to <https://github.com/gorhill/httpswitchboard/issues/231>.
    * The workaround rule `@@||docs.google.com/stat|$xmlhttprequest[,...]` will be removed for you by HTTPSB in order to ensure the formerly problematic block rule in _EasyPrivacy_ is now properly enforced.

***

### 0.9.8.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.8.0.zip) date: 15 June 2014
- Revised extension shortcuts:
    * Shortcut names can be internationalized.
    * **"Open dashboard..."** (Alt-S) (will go to whatever tab is open in the dashboard, or the _Settings_ tab)
    * **"Temporarily whitelist all"** (Alt-A).
        - This is equivalent to whitelisting the `all` matrix cell. Because whitelisting the `all` cell is a drastic action, a domain-level scope is automatically created beforehand so as to avoid whitelisting the whole internet.
    * **"Temporarily whitelist page domain"** (Alt-W).
        - This is equivalent to whitelist the domain cell of the current web page.
    * **"Remove all temporary changes"** (Alt-Q).
        - This will remove _all_ temporary changes.
    * Chrome API allows only a maximum of four shortcuts per extension, so I had to choose carefully what I think are the most useful shortcuts.
- External assets are now updated automatically.
    * _"External assets"_ are those you can see listed in the _"About"_ tab in the dashboard.
    * External assets are automatically updated when the extension launches; or every five days thereafter.
    * You can still force an update in the _"About"_ tab, or you can just forget about looking whether updates are available, it will be all taken care for you.
    * In order to harden update feature so that a user does not end up with corrupted files, I worked on, and spun off a [standalone MD5 hashing library](/gorhill/yamd5.js) (in case whoever is interested).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/338>: "Quick heads-up: Update Punycode".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/334>: "Automatic update of ubiquitious lists".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/263>: "Handle properly error pages returned when fetching `assets/checksums.txt`".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/248>: "Erasing (for single scope) resets to default global scope rule (the one that the extension uses in new install)".
    * Now the generic rules from global scope will be used rather than the hard-coded factory rules.

***

### 0.9.7.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.7.1.zip) date: 10 June 2014
- Added more ABP-filter lists. Titles:
    * "Adblock Plus Lithuania"
    * "Adblock Polska"
    * "Icelandic ABP List"
    * "Greek AdBlock Filter"
    * "Filtros Nauscopicos"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/333>: "Necessary script for frame not shown in the matrix".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/330>: "ABP rules blocking images can't be unblocked".

***

- 4 June 2014
- Updated reference benchmark with [results for new blockers](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites#june-4-2014).
    * Privacy Badger was properly primed this time.

***

### ~~The end~~
- Can't help it: I keep wondering how to improve it.
- Priority: To not let feature creep turn this into a mess.

***

### 0.9.7.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.7.0.zip) date: 2 June 2014
- I consider this a new version because of how [issue #303](/gorhill/httpswitchboard/issues/303) was fixed (_"Support `file://` protocol"_):
    * URI schemes other than `http` or `https` used to be reported in the behind-the-scene matrix.
    * Now these schemes will be reported on the page where they occurs, and `{schemename}-scheme` will be used as the hostname for scope selection. Examples:
        - A `file:///...` URI will be reported as a `file-scheme` scope in the matrix.
        - A new tab in Chromium is reported as a `chrome-scheme` scope.
        - A new tab in Opera is reported as a `opera-scheme` scope.
        - A `data:...` URI is reported as a `data-scheme` scope.
        - A `chrome-extension://...` URI is reported as a `chrome-extension-scheme`.
        - Etc.
    - Inline javascript cannot be disabled for pages with scheme other than `http` and `https`.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/325>: "Google search ads not block in 'Adblock emulation mode'".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/321>: "Improper handling of IP addresses in the matrix".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/303>: "Support `file://` protocol".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/246>: "Matrix: header row should always be present".

***

### 0.9.6.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.6.0.zip) date: 28 May 2014
- [Chinese (Simplified) translation](/gorhill/httpswitchboard/commit/deab1cbfd756782b76f566ab4d80be1ffc3b33ac) by [noblehng](/noblehng).
    * So this fixes [issue #71](/gorhill/httpswitchboard/issues/71)

***

### 0.9.5.6
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.6.zip) date: 28 May 2014
- As part of [fix to #218](/gorhill/httpswitchboard/issues/218), the built-in list of block lists can now be updated without waiting for a new release of the extension.
    * Essentially this means I can add new (or remove obsolete) lists and users will be able to start to use these new lists after updating assests, rather than having to wait for a new release of the extension.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/316>: "download attachment in gmail"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/218>: "Friendly names for lists of ubiquitous blocked hosts"

***

### 0.9.5.5
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.5.zip) date: 27 May 2014
- Normally when assets are merely updated, no new revision is necessary, but in the current case a new list has been added (ABP Japnese filter), so the revision was necessary.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/312>: "Add recipe for Twitch.tv"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/309>: "Add inmuiads.info in HTTP Switchboard's self maintained blacklist"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/308>: "ABP Japnese filter request"

***

### 0.9.5.4
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.4.zip) date: 26 May 2014
- More translation work by [tlu1024](/tlu1024) (German), [r35p3ct](/r35p3ct) (Russian), and [tailHey](/tailHey) (French)
- Fixed <https://github.com/gorhill/httpswitchboard/issues/306>: "Number of blocked script not counted properly for global stats"

***

### 0.9.5.3
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.3.zip) date: 25 May 2014
- [Lot of translation work](/tlu1024?tab=activity) by [tlu1024](/tlu1024) (German)
- Fixed <https://github.com/gorhill/httpswitchboard/issues/299>: "Frame transparency doesn't work for the whole replacement frame"
    * Your current choice of color/opacity will be reset to factory setting. Sorry.
    * I had no choice but to change the internal representation of the color information, and trying to ensure backward compatibility would have required way too much complicated code, and in general the rule is more code = higher likelihood of new bugs. I went with the safer option.
    * Since now opacity setting is separate from color setting, you don't have to enter a "CSS color", the built-in widget for color picking can now be used.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/52>: "Make matrix colors work for color blind people"
    * I can't tell whether it is good enough, so I will await feedback from color-blind people.
    * I couldn't use patterns, as the cells and the permanent state indicators are too small for patterns. So I went with shades of grays.

***

### 0.9.5.2
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.2.zip) date: 25 May 2014
- [Translation work](/gorhill/httpswitchboard/commit/a4be5beeed6b18446e5cd5fc2c6cd50c75c0f658) by [r35p3ct](/r35p3ct) (Russian).
- [Translation work](/gorhill/httpswitchboard/commit/f27a13a9a6c97516fa24c4f48d15d7966111651b) by [tlu1024](/tlu1024) (German).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/300>: "Built-in Chinalist needs update"
    * Apparently the other China list in there is not updating anymore, so I will remove it at some point.

***

### 0.9.5.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.1.zip) date: 24 May 2014
- [Translation work](/gorhill/httpswitchboard/commit/e990fae66190f8ded4fd0ff326b2adc98dd732f0) by [tailHey](/tailHey).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/260>: "Ad blocking differs from Adblock with the same rules" (this was [not the same bug](/gorhill/httpswitchboard/issues/260#issuecomment-44000577) as the original issue).

***

### 0.9.5.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.5.0.zip) date: 23 May 2014
- **New feature:** When installing the extension for first time, users will be presented with a list of "flavoured" configurations to help them get started
    * _Breakage_ refers to the likeliness of web pages to not render and/or behave as expected
        - _Block all / allow exceptionally_ (default mode) => Security: very high, Breakage: high
        - _Allow all / block exceptionally_ => Security: medium, Breakage: medium low
        - _Ad blocker-like_ => Security: low, Breakage: low
        - _NoScript-like_ => Security: high, Breakage: high
        - _RequestPolicy-like_ => Security: medium high, Breakage: high
        - _Block nothing / report everything_ => Security: none, Breakage: none
    * These are merely starting points, user can customize at will afterward
    * For users who already have an existing implementation, this setup page can still be accessed from the _About_ tab in the dashboard: click the _Start from scratch..._ button.
    * **Important:** Keep in mind that loading a predefined configuration is similar to restoring all your settings and data, which means everything will be overwritten.
        - So if you just want to just _try_ these configurations, be sure you have a back up of your data.
- Fixed a bug in the parsing of cosmetic filters which prevented exception filters to work.

***

### 0.9.4.4
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.4.4.zip) date: 21 May 2014
- Coverage of cosmetic filters (ABP "element hide" filters) is now 100%.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/286>: "Add pub2srv.com in HTTP Switchboard's self maintained blacklist"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/283>: "Make the cosmetic filter rule injection more efficient for long running dynamic pages"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/276>: "Improve coverage of ABP cosmetic filters"
- Fixed <https://github.com/gorhill/httpswitchboard/issues/260>: "Ad blocking differs from Adblock with the same rules"

**And while I have your ear,** I want users to be reassured that the new cosmetic filters feature is **not** a _"broken implementation"_ [as suggested by Wladimir Palant](https://bugzilla.mozilla.org/show_bug.cgi?id=988266#c39). **It's pure fabrication.**

Similarly, his _"potentially significant hang when the page loads"_ "concern" is pure nonsense, given that ABP does magnitudes worst to inject its thousands of CSS rules. In worst case scenarios, HTTPSB does at most a couple hundreds iterations, which consist of [tightly optimized look-up operations](/gorhill/httpswitchboard/blob/master/js/abp-hide-filters.js#L514) (fast) in order to narrow the number of CSS rules to inject to a handful.

Injecting the CSS rules **IS** the expensive operation, hence you want to minimize this as much as possible. ABP injects 20,000 of these CSS rules indiscriminately, so expressing "concerns" that HTTPSB _may_ end up looping 500 times performing fast look-up operations is just plain intellectual dishonesty.

Everything is [in the open on Github](/gorhill/httpswitchboard/commits/master), with time stamps, etc. Any developer who can read javascript will be able to confirm everything I wrote in [my original article](/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption). I wish this will happen.

My only mistake was to think the ABP developers would be happy I found and shared a solution to their problem of **indiscriminately** injecting 20,000 CSS rules on every page and frames on that page.

***

### 0.9.4.3
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.4.3.zip) date: 20 May 2014
- [Translation work](/gorhill/httpswitchboard/commit/7ec845f1453cb7b068d18c5e410a5cb336b0aab5) by [r35p3ct](/r35p3ct)
- Fixed <https://github.com/gorhill/httpswitchboard/issues/283>

***

### 0.9.4.2
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.4.2.zip) date: 19 May 2014
- Increased coverage of cosmetic filters (ABP element hiding filters) to 99%.
- Added support to make cosmetic filters friendly to pages which have dynamically loaded content.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/261>
    * Thanks to [my-password-is-password](/my-password-is-password) for his precious help in tracking the bug.
- Contributions by [Landpaddle](/Landpaddle):
    * <https://github.com/gorhill/httpswitchboard/pull/281>
    * <https://github.com/gorhill/httpswitchboard/pull/279>
- Contributions by [deverton](/deverton):
    * <https://github.com/gorhill/httpswitchboard/pull/274>

***

### 0.9.4.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.4.1.zip) date: 18 May 2014
- Fixed a couple of quirks ([here](/gorhill/httpswitchboard/commit/c8cd9c55bc5dccd40ac0a2064e0599ac6fe8a189) and [here](/gorhill/httpswitchboard/commit/8aff8064193db6c90b200af7d2445f2bb9d8bf2f)) in the implementation of ABP cosmetic filters.
    * It doesn't affect at all benchmark results [shown there](/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption)).

***

### 0.9.4.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.4.0.zip) date: 18 May 2014
- **New feature:** Support for ABP cosmetic filters (aka ""element hiding" filters).
    * The reason I changed my mind: [Adblock Plus memory consumption](/gorhill/httpswitchboard/wiki/Adblock-Plus-memory-consumption).
    * Disabled by default.
    * Enable in the _Ubiquitous rules_ tab.
    * Coverage of ABP cosmetic filters is currently nearly 87%. I will add more as time permits.
    * Currently I measured that over 20,885 cosmetic filters are parsed and enforced, while the total is 24,087 (as of writing).
    * Just in case: the better performance has nothing to do with the fact that coverage is currently 87% instead of 100%.
    * Test page: <http://simple-adblock.com/faq/testing-your-adblocker/>

***

### 0.9.3.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.3.0.zip) date: 17 May 2014
- **New feature:** Due to popular demand, I added a new option in the _Settings_ tab: _"Blocked frames color (any valid CSS color):"_ along with a text input field to enter a valid CSS color value.
    * Default is `rgba(204, 0, 0, 1)`, i.e. as it was before internally.
    * Example of valid CSS color values: `silver`, `#c00`, `rgba(192, 192, 192, 0.2)` (note the opacity value), etc.
    * Reference for CSS color: <http://www.w3.org/TR/css3-color/#html4>
    * **Beware:** I personally believe that hiding blocked frames from view is a bad idea (hence my resistance to implement the feature). So whether blocked frames are visible or not is now completely up to you.
    * If you really want to completely render invisible blocked frames, the CSS color name is `transparent`.
    * As of now there is **no** code to validate whether the CSS color you enter is valid. If is not valid, result will likely be invisible blocked frames, so be careful.
    * To reset to factory color, just empty the input filed and press return: the field will be filled with factory color `rgba(204, 0, 0, 1)`.
    * I have to admit, it is a nice feature to have... I ended using it, my color: `rgba(204,204,204,0.8)`.
    * **Note:** After v0.9.3.0 was published, [my-password-is-password](/my-password-is-password) [found a fix](/gorhill/httpswitchboard/commit/6525a93bc6703e19ee3a1014806c84abff5e049b#commitcomment-6360130) for the slight visual glitch visible in the pattern. It's not worth to release a new revision just for this, but I will include the fix in the next release.
- More work on performance and code review.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/135>: "Change the colour of the blocked frame to grey".

***

### 0.9.2.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.2.1.zip) date: 16 May 2014
- This revision accommodates Opera web store.
- No issue fixed, but as the extension is heading toward version 1.0, I will spend more time code reviewing (and making changes if needed), benchmarking (memory, cpu), etc.
- For technically minded individual, changes can be seen in the [commit history](https://github.com/gorhill/httpswitchboard/commits/master) (I can't open an issue for every little code revision resulting from above-mentioned code review).

### 0.9.2.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.2.0.zip) date: 14 May 2014
- Big news for Russian users: [Russian translation](/gorhill/httpswitchboard/commits/master/_locales/ru/messages.json) landed by [r35p3ct](/r35p3ct) (That's quite a lot of work in one swoop. Thanks!)
    - Including further contributions by [extesy](/extesy)
- With [issue #231](/gorhill/httpswitchboard/issues/231) now fully addressed, coverage of ABP complex filters is now 99.7%.
    * Because of this, ABP filtering engine is now enabled by default for new installations.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/261>: "Front page on www.tsn.ca goes blank when user agent spoofing is enabled".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/259>: "Performance: single char hash for ubiquitous hostnames in matrix filtering".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/231>: "More complete support of Adblock filters".

***

### 0.9.1.2
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.1.2.zip) date: 10 May 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/258>: "Adblock+ complex filters not working".
    * Given the size this project reached, I think I am at the point where I will have to ask for a couple of volunteers (5?) to test draft versions before I officially release a version or revision.

***

### 0.9.1.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.1.1.zip) date: 9 May 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/257>: "cookies dropped randomly since yesterday".
    * I screwed up, a reverse logic mistake caused session cookies to be systematically removed for users who had the _"Delete non-blocked session cookies..."_ option disabled.

***

### 0.9.1.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.1.0.zip) date: 8 May 2014
- New feature: In order to enable users to help each other more easily, users can exchange matrix recipes with each other.
    * ![Reciper](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-reciper.gif)
    *  The rationale is to decentralize support for the extension, I expect there will always be advanced users somewhere ready to help novice users, and this feature is to make helping easier.
    * The new widget allows to export the current state of the matrix into a _recipe_, and allows to import a recipe into the current matrix. Example:
        - Novice user asks help for set of rules to "unbreak" a web site.
        - Advanced user figures the minimal set of rules.
        - Advanced user exports the state of the matrix into a recipe.
        - Advanced user post the resulting recipe somewhere where the novice user can copy it.
        - Novice user, trusting advanced user, copy-paste the recipe into the recipe field and click on the import button.
        - Novice user tries if it works, and if so, clicks on the padlock to lock down the new rules.
        - Novice user express his gratitude to advanced user, advanced user answers "no problem".
    * The import tries to be "smart", i.e. it won't allow the import of rules which are irrelevant to the current matrix.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/255>: "A session cookie may be removed before it expires".
    * Typical symptom: randomly being logged out of whatever web site you were logged in (not fun).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/252>: Mismatch between user agent string from HTTP header and user agent string from `window.navigator.userAgent`.
- Progress on <https://github.com/gorhill/httpswitchboard/issues/231>: "More complete support of Adblock filters"
    * Whitelist filters now supported.
    * Coverage of ABP filter syntax is still not complete, but the support of whitelist filters bumps up the coverage from 84.5% to 87.9% in the case of EasyList + EasyPrivacy.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/81>: "Figure a way to allow 'snapshot' of pop-up matrix into a recipe".

***

### 0.9.0.0

- **I care about backward compatibility,** but apparently I failed this time. It has come to my attention that a user had its settings for auto-create scope disabled, despite me having put [code in there](/gorhill/httpswitchboard/blob/master/js/storage.js#L53) to translate the old internal setting into the new one. ~~I still do not understand how this code can fail, but in any case,~~ **my apologies for this fumbling.** (I could fix the problem, but I suppose it is too late at this point, so simplest workaround is to go to the _Settings_ tab a re-select your choice of scope auto-creation -- `domain` is now the preferred choice.)
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.9.0.0.zip) date: 27 April 2014
- Changed feature: You can now choose to auto-create domain- or site-level scopes (before only site-level scope was available).
    * I figure this was required as in general, a domain-level scope offers an optimal balance between usability and security.
    * The security gain from using global scope to using a domain-level scope is huge.
    * The security gain from using a domain-level scope to using a site-level scope is marginal in most cases.
    * The convenience gain of using a domain-level scope rather than a site-level scope is significant.
    * For instance, it is quite common for a web site which requires logging in to use HTTP redirect directives from one subdomain to another.
        - Example: log in on `login.example.com`, end up on `members.example.com`.
        - With a site-level scope set to `login.example.com`, the login operation would fail because whatever whitelist rules were created in the `login.example.com` scope do not apply to the `members.example.com` scope.
        - This is where domain-level scope is great, as whatever whitelist rules created in `*.example.com` apply both to `login.example.com` and `members.example.com`.
        - A real life example of this particular issue was raised recently: <https://github.com/gorhill/httpswitchboard/issues/249> (French).
    * Therefore aute-creation of domain-level scopes is now considered the preferred way of using HTTPSB. Defaults are left unchanged though, as I want to further evaluate whether auto-scoping should be enabled out of the box.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/250>: "Let the user choose whether site- or domain-level scopes should be auto-created".

***

### 0.8.9.3

- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.9.3.zip) date: 25 April 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/244>: "'HTTP cookie headers foiled' repeated twice in the Statistics tab".
    * The second entry was supposed to be "HTTP referer headers foiled"

***

### 0.8.9.2

- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.9.2.zip) date: 25 April 2014
- Added [RU AdList](https://code.google.com/p/ruadlist/), a list of ABP filters for Russia (list copied from <https://easylist-downloads.adblockplus.org/advblock.txt>).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/242>: "Requests showing up as blocked and allowed in Statistics Request log".
    * Just to reassure users, the flaw was in the **reporting** of javascript files in the request log when blocked through ABP filtering: the files were properly blocked, they were just wrongly reported as "allowed".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/241>: "Wrong display of 0% in Statistics tab (ABP complex filters)".

***

### 0.8.9.1

- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.9.1.zip) date: 25 April 2014
- Workaround for <https://github.com/gorhill/httpswitchboard/issues/240>: "Privacy check box doesn't save [in Chrome 36 dev, Chrome 34 is ok]" ([see chromium bug #366989](https://code.google.com/p/chromium/issues/detail?id=366989))
- [Traduction de la fonctionnalité User-Agent](/gorhill/httpswitchboard/commit/ca55a2564d944e6955346791b628b2a7c4a23e2c) par [tailHey](https://github.com/tailHey)

***

### 0.8.9.0

- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.9.0.zip) date: 24 April 2014
- New privacy feature: [User-Agent spoofing](https://en.wikipedia.org/wiki/User_agent#Possible_privacy_issue).
    * Available in the _Settings_ tab:
        - Enable/disable (disabled by default)
        - An input field to choose at which interval (minutes) to randomly pick a new user agent string
        - A text area so you can enter your own list of user agent strings from which to randomly pick
            * Enter nothing to blank the user agent string (not recommended)
            * Enter a single user agent string to force a particular one
            * Enter many to cycle randomly through them, as per your supplied interval
            * I put in a couple of default user agent strings I found while browsing around, but I suggest you pick your own user agent strings going forward. There are various sources out there: you choose.
            * Don't go overboard with the number of user agent strings, a handful of the top most common strings is just enough to accomplish the purpose.
            * Prefixing a line with `#` will cause the line to be ignored
    * Of interest: [_EFF_: "Browser Versions Carry 10.5 Bits of Identifying Information on Average"](https://www.eff.org/deeplinks/2010/01/tracking-by-user-agent)
- Version française maintenant complète après la [révision finale de tailHey](/gorhill/httpswitchboard/commit/b6e094844433a3709c2e861b41218158eea601d4)
- Fixed <https://github.com/gorhill/httpswitchboard/issues/100>: "Ability to neutralize User-Agent string for enhanced privacy" (as per above)

***

### 0.8.8.2

- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.8.2.zip) date: 23 April 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/239>: "ABP filters not working when there's an uppercase letter"
    * ABP filters are now case insensitive.
- Internationalization infrastructure work
    * I can say that finally HTTPSB is fully ready for translation, although I expect there might be small bits here and there that I missed. The translation work in whatever language itself is left to volunteers.

***

### 0.8.8.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.8.1.zip) date: 21 April 2014
- French translation [work](/gorhill/httpswitchboard/commit/8cefe17645de9076dd0cfbdfacf93873f84b1b77) by [tailHey](https://github.com/tailHey).
- Removed [obsolete portion of text](/gorhill/httpswitchboard/commit/dc95785c8f52d0f64520e1148eb9daccdb939d9d) in _Settings_ tab regarding behind the scene filtering.

***

### 0.8.8.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.8.0.zip) date: 21 April 2014
- New option in the _Settings_ tab: "Auto delete unused temporary scopes".
    * Disabled by default.
    * Especially useful for users who have enabled "Auto create temporary site-level scopes".
    * A temporary scope (which has no permanent counterpart) won't be deleted _immediately_ after the web page for which it applies is closed. It will linger a bit, and if it still unused after 20 minutes or so, it will then be removed from memory.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/229>: "Auto-reload only current tab".
    * The user has now the choice to smart reload: _None_, _Current_, or _All_ (default).
    * Just a reminder: smart reload ensures that **only** the pages which are affected by a change in the matrix will be reloaded. The feature here gives the user the choice of which set of pages are going to be candidates for smart reload.
- I changed the appearance of the filtering switches when in their _off_ state: These switches are kind of important, so they need to stand out more if switched off.

***

### 0.8.7.1
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.7.1.zip) date: 18 April 2014
- Fixed <https://github.com/gorhill/httpswitchboard/issues/237>: "Do not auto-create site-level scope if matrix filtering for global scope is off".

***

### 0.8.7.0
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.7.0.zip) date: 18 April 2014
- The master switch is gone.
- A new ["matrix filtering" switch](/gorhill/httpswitchboard/wiki/The-matrix-filtering-switch) is now available, and it is scope-based (see it as a master switch, but it applies only to the current scope).
    * Since now matrix filtering can be turned off for a specific scope, the chromium-behind-the-scene scope will come out-of-the-box with matrix filtering turned off, in order to guarantee that, out-of-the-box, HTTPSB does not interfere with the browser or other extensions.
    * There were cases of [extensions being broken by HTTPSB](http://blog.martinkadlec.eu/post/501-smart-rss-final-v10#comment-4645) *despite* the chromium-behind-the-scene scope defaulting to allow-all/block-exceptionally, because some of the hostnames the user was feeding another extension were ubiquitously blacklisted.
    * For existing users, matrix filtering will be on by default for all scopes, including the chromium-behind-the-scene scope, to ensure there is no change in behavior with your existing installation.
- Adblock Plus filter syntax is now supported as user-supplied ubiquitous rules.
    * You can mix and match plain hostname rules with Adblock Plus filter rules.
    * "One hostname per line" becomes "One rule per line".
    * Respect [proper and sane ABP-filter syntax](https://adblockplus.org/en/filter-cheatsheet) and all should be fine.
        - Remember: garbage in, garbage out, so if you feed HTTPSB garbage rules, HTTPSB's behavior as a result is undefined.
    * Be mindful that [not all ABP filter syntax is supported](/gorhill/httpswitchboard/wiki/Net-request-filtering:-overview#abp-filtering).
- The HTTPSB entries in the browser's contextual menu (right-click) have been removed: I found out they were not working correctly due to the many changes which have happened since the contextual menu code was released. More thoughts are needed before I fix and put back these contextual menu entries. Probably not many users were relying on the contextual menu since nobody reported it wasn't working properly.
- New wiki page for an overview of [HTTPSB's filtering engine](/gorhill/httpswitchboard/wiki/Net-request-filtering:-overview)
- Fixed <https://github.com/gorhill/httpswitchboard/issues/234>: "Per-scope switch to disable all ubiquitous blocked hosts".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/232>: "Allow user to supply his own ADP-compatible filters".

***

### 0.8.6.4
- [Release](/gorhill/httpswitchboard/blob/master/dist/httpswitchboard_0.8.6.4.zip) date: 15 April 2014
- No changes for existing users.
- Removed Fanboy lists from out-of-the-box default selected ubiquitous lists. Because [this](http://www.wilderssecurity.com/threads/http-switchboard-for-chrome-chromium.356427/page-26#post-2362143).
    * I personally use the Fanboy lists, however these are causing a bit too much material to be blocked, especially annoying for a new user who chooses to use HTTPSB in [allow-all/block-exceptionally approach](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#the-allow-allblock-exceptionally-approach).

***

### 0.8.6.3
- Fixed <https://github.com/gorhill/httpswitchboard/issues/226>: "Overzealous ABP filtering: `||` needs to match beginning of domain name".
    * More accurately, `||` needs to match the start of a label in a hostname. The bug blocked needed CSS files on <http://lifehacker.com>, <http://gawker.com>, etc. because there was a false positive for an ABP complex filter (URLs from `c.kinja-static.com` were erroneously reported as matching `||a-static.com^` filter).

***

### 0.8.6.2
- Fixed <https://github.com/gorhill/httpswitchboard/issues/225>: "`slashdot.org` site is blocked when using `fanboy-annoyance.txt`".
    * HTTPSB now supports the parsing and enforcement of the [ABP's `third-party` filter option](https://adblockplus.org/blog/recognizing-third-party-content) for ABP complex filters.

***

### 0.8.6.1
- Fixed <https://github.com/gorhill/httpswitchboard/issues/224>: "_Restore from file_ doesn't always restore a user's custom ubiquitous rules".

***

### 0.8.6.0
- Fixed <https://github.com/gorhill/httpswitchboard/issues/195>: "Need an 'export all'/'import' feature".
    * New buttons, in the _About_ tab: *Backup to file...* and *Restore from file...*
    * When restoring, **ALL** existing settings, rules, etc. will be **overwritten**, and the extension will be restarted.
    * Be mindful that the backed up data is saved as a `text/json` file, hence it is directly human readable. Take appropriate measures (back up to an encrypted drive or folder, etc.) if you have privacy concerns.
    * Saving to cloud-based "Chrome Sync" storage is not implemented, due to the [limits imposed on size](https://developer.chrome.com/extensions/storage#property-sync).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/115>: "Ability to make global rules".
    * The ability to create ubiquitous whitelist rules, i.e. the whitelisting of hostnames in all scopes.
    * A new section at the bottom of the _Ubiquitous rules_ tab as been added, where the user can provide his own list of hostnames which are to be ubiquitously whitelisted, i.e. whitelisted in all scopes.

***

### 0.8.5.6
- Fixed <https://github.com/gorhill/httpswitchboard/issues/215>: "Necessary script in frame not shown in matrix".
    * This bug would show up specifically if a user had the Chromium settings *"Block third-party cookies and site data"* enabled.
    * This caused the user to lack the necessary information about the number of scripts attempting to execute within embedded frames (if and once these were unblocked).

***

### 0.8.5.5
- Fixed <https://github.com/gorhill/httpswitchboard/issues/219>: "Number of requests over-reported in matrix".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/217>: "Add Wiltteri, the finnish supplement list for EasyList to HTTPSB".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/207>: "Flush cached 3rd-party assets when a new version is installed".
    * Before this fix, 3rd-party assets were still deemed out-of-date after an update even when a new version was shipped with the most up to date assets.

***

### 0.8.5.4
- Fixed <https://github.com/gorhill/httpswitchboard/issues/207>: "Youtube may not be whitelisted during first install for Opera".

***

### 0.8.5.3
- Fixed <https://github.com/gorhill/httpswitchboard/issues/213>: "HTTPSB's "power switch" not working anymore."
- Fixed <https://github.com/gorhill/httpswitchboard/issues/32>: "Build matrix incrementally."
- (I will be working more on bug fixes and language support framework for the time being.)

***

### 0.8.5.2
- Fixed <https://github.com/gorhill/httpswitchboard/issues/211>: "Hostnames with underscores not parsed properly."

***

### 0.8.5.1
- Fixed <https://github.com/gorhill/httpswitchboard/issues/210>: "Not all hostname-compatible rules from ABP files imported as HTTPSB blocked hostname".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/209>: "Details in Statistics Page not working correctly".

***

### 0.8.5.0
- New button in the matrix pop-up which allows to turn on/off filtering using Adblock Plus ("ABP") complex filters for a specific scope.
    * ![ABP filtering button](https://f.cloud.github.com/assets/585534/2400994/85c8c4fc-aa10-11e3-8db5-140d8a8fb2ee.png)
    * The state of this button is saved as part of a scope when you lock down your changes.
    * The number in the badge represents to total number of requests blocked on the page using ADP filtering.
- The state of the padlock (to persist changes) and eraser (to revert changes) buttons now reflect the number of temporary changes (including the ABP button) which are not persisted in the current matrix.
- Net requests blocked through ABP filtering are now identifiable by a special icon in the request log in the _Statistics_ tab in HTTPSB's _Dashboard_: by hovering the mouse over that icon you can see which ABP rule specifically is responsible for the blocking.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/208>: "Adblock Plus filtering is still in effect even after turning off HTTPSB".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/205>: "Need a way to easily exclude a whole page or domain from ABP-filtering".
- Fixed <https://github.com/gorhill/httpswitchboard/issues/189>: "Provide a badge for other toolbar icons in popup menus".

***

### 0.8.4.8
- Fixed newly added assets not being added: <https://github.com/gorhill/httpswitchboard/issues/206>.
- Code improvement: <https://github.com/gorhill/httpswitchboard/issues/204>.
    * <http://jsperf.com/old-uritools-vs-new-uritools>.
- Fixed Hangouts extension not working: <https://github.com/gorhill/httpswitchboard/issues/91#issuecomment-37180275>.

***

### ~~0.8.4.3~~ ~~0.8.4.4~~ ~~0.8.4.5~~ ~~0.8.4.6~~ 0.8.4.7
- Sorry for the many spurious versions between 0.8.4.3 and 0.8.4.7 (Chrome store doesn't allow uploading a package without changing the version number):
    * There was an issue I had a hard time to figure, which I narrowed to a [file name in the 3rd-party assets with a reserved character as per Windows rules for filenames](/gorhill/httpswitchboard/commit/cb0016f53d171b0a0ea464d75b6f76840784db72) (I develop on Linux, so I had a bit of a hard time figuring the issue from the [generic error message](http://stackoverflow.com/questions/15259125/developer-chrome-extension-package-is-invalid-details-could-not-uzip-extensi#) reported by the Chrome store.
- Support for ABP complex filters with wildcards.
    * This adds more than 2,000 filters being in use when loading the default ABP lists.
- Added more lists of ABP filters in the _Ubiquitous rules_ tab.
    * These new lists are all disabled by default, as the usefulness of these lists depends on location/language.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/202>.

***

### 0.8.4.2
- Fixed a bug which could potentially occur when loading the various ubiquitous lists, causing the extension to break:
    * <https://github.com/gorhill/httpswitchboard/issues/199>.
    * The bug would occurs depending on how fast the lists are loaded into memory: slower = bug more likely to occur.
    * Workaround for those still using version 0.8.4.1 is to disable the "Parse and enforce Adblock+ complex filters" feature.
    * Sorry :-(
- Further performance and memory footprint improvements to the code dealing with Adblock Plus complex filters.
    * Reaching optimal performance is a requirement in order to support more complex filter syntax, i.e. wildcards, options, etc.

***

### 0.8.4.1
- Fixed potential false negatives (in rare circumstances) when evaluating against Adblock+ complex filters.
- Simplified Adblock+ complex filters-related code.

***

### 0.8.4.0
- First, an apology for having [dismissed too quickly a good suggestion](https://github.com/gorhill/httpswitchboard/issues/149#issuecomment-32458730) a while ago.
- Adblock Plus ("ABP") complex filters (those which parse into more than just "block a whole domain") can now be parsed and used to block web requests:
    * Optional, disabled by default. Can be turned on from _Ubiquitous rules_ tab in the _Dashboard_.
    * Consider this a beta feature.
    * Especially handy for users who prefer to work in [allow-all/block exceptionally](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach) mode
    * Not all ABP complex filters are parsed:
        - Those with [options](https://adblockplus.org/en/filters#options) are currently ignored (working on it, as time permit).
        - Those with [regular expressions](https://adblockplus.org/en/filters#regexps) are currently ignored (probably will support partially, i.e. `*` only): these are rare instances and their use is discouraged anyway).
        - Filters used to [hide elements](https://adblockplus.org/en/filters#elemhide) are ignored (undecided whether I will ever implement since it requires modifying the DOM).
        - Filters used to whitelist something -- like ["acceptable ads"](https://adblockplus.org/en/acceptable-ads) -- are ignored (will never implement).
    * ABP complex filters are **not reflected in the matrix** (except obviously for those which apply on a whole domain). There is no user interface to enable/disable a single ABP complex filter.
        - Rules from HTTPSB have precedence. If a request is evaluated as "allowed" by HTTPSB, it is then further evaluated using ABP filters.
        - The only way to disable a single ABP complex filter is to disable the parsing of all complex filters, or to disable the whole list in which the filter appears. ABP complex filters are not affected by preset recipes.
        - The number of requests effectively blocked by complex ABP filters is reported in the _Statistics_ page in the _Dashboard_, so that you can get a sense of whether ABP filters are worth parsing and enforcing, given the extra memory use.
        - The added overhead of evaluating an ABP complex filter is small, around 30 µs. (I did not revise [this](https://github.com/gorhill/httpswitchboard/wiki/Doesn't-HTTPSB-add-a-significant-overhead-to-network-traffic%3F) yet to reflect the new timings.)
    * The main point of this feature is that you are still using ABP along HTTPSB, HTTPSB gets closer to be a complete replacement solution to ABP.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/198>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/197>.

***

### 0.8.3.0
- Assets used by HTTPSB can now be updated without having to wait for a new release of the extension.
    * From the _About_ tab of the extension's _Dashboard_.
    * "Assets" refers to:
        - Preset ubiquitous blacklists.
        - Preset recipes.
        - [Public Suffix List](http://publicsuffix.org/list/).
- Significantly reduced memory footprint.
    * Not that there wasn't any memory leak, just that for this release, I chose to spend more time on code revision and refactoring instead of just features -- a necessary recurring task in order to ensure the code doesn't drift too far away from sanity. This allowed me to put to test and validate some ideas I was entertaining since a long time regarding memory footprint.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/179>.

***

### 0.8.2.1
- Fixed <https://github.com/gorhill/httpswitchboard/issues/191>
    * First two definitions:
        - "Tabless HTTP requests" are requests which do not originate from any particular tab: these are known as [behind-the-scene requests](/gorhill/httpswitchboard/wiki/Behind-the-scene-requests).
        - "Orphan HTTP requests" are requests originating from a valid tab, but which tab display the content of a URL which is not handled by HTTPSB, i.e. `opera://startpage/`, or whatever else similar which may come in the future.
    * Orphan HTTP requests are now categorized as behind-the-scene requests.
        - Before the fix, these requests were evaluated against the global scope, but unfortunately they could not be reported in any matrix.

***

### 0.8.2.0
- New option in _Settings_ page to enable/disable smart auto-reload (as per [issue #94](/gorhill/httpswitchboard/issues/94)). Enabled by default.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/193>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/192>.
- Addressed <https://github.com/gorhill/httpswitchboard/issues/191>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/94>.

***

### 0.8.1.3
- Workaround for Yandex's improper rendering of float element in toolbar of extension pop-up.

***

### 0.8.1.2
- Fixed auto-whitelisting of Youtube at install time for Opera 19.

***

### 0.8.1.1
- Minor revision: The mini pop-up menu in the pop-up of the extension giving access to _Rule manager_, _Settings_, _Documentation_ and _On/off_ buttons has been removed and the buttons are now directly accessible in the extension pop-up toolbar as _Dashboard_, _Documentation_ and _On/off_ buttons on the far right.

***

### 0.8.1.0
- **New permission required:** ["unlimitedStorage"](https://developer.chrome.com/extensions/declare_permissions#unlimitedStorage).
    * This permission gives an extension access to a virtual, sandboxed file system.
        - Currently quota set at [maximum of 24 MB](/gorhill/httpswitchboard/blob/master/js/assets.js#L55), because the size of the content of [assets directory](/gorhill/httpswitchboard/tree/master/assets) (updated versions of files in this directory will eventually be stored in the sandboxed file system) is roughly 17 MB.
    * This is needed in order to allow users to provide their own ubiquitous list of blacklisted hosts.
    * This is also required for the upcoming feature which will allow users to update themselves the various data used by HTTPSB without having to wait a new version of HTTPSB:
        - [Third-party blacklists](/gorhill/httpswitchboard/tree/master/assets/thirdparties).
        - [Preset recipes](/gorhill/httpswitchboard/tree/master/assets/httpsb).
        - [Mozilla's Public Suffix List](http://publicsuffix.org/list/).
- Redesigned extension pages: All extension pages are now accessible through tabs on a single dashboard page ([issue #129](/gorhill/httpswitchboard/issues/129)).
    * The list of third-party lists of blocked hosts has moved to the _Ubiquitous rules_ tab.
        - "Ubiquitous" because these rules apply in all scopes.
    * The former _Rule manager_ page has been renamed _Scoped rules_.
- Users can now supply their own list of ubiquitous blacklisted hosts (go to _Ubiquitous rules_ tab in the dashboard).
    * This fixes one half of [issue #152](/gorhill/httpswitchboard/issues/152), the other half being ["ubiquitous whitelisted hosts"](/gorhill/httpswitchboard/issues/115).
    * The project's mini-blacklist `assets/httpsb/block-facebook.txt` is gone. If you were using it, just enter the [content of the file](https://raw2.github.com/gorhill/httpswitchboard/master/assets/httpsb/block-facebook.txt) in your user list.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/181>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/129>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/39>

***

### 0.8.0.1
- Replaced all preset recipes for Google various services with one single preset recipes which "unbreak" all Google various services.
    * Turns out, it's just way too much time-consuming to try and create specific set of rules for _each_ specific Google service.
    * At least, it is scoped, so Google servers won't be pinged when not on a Google-owned web page.
    * That's the point of domain-level scopes anyway, so I will just use one for Google.

***

### 0.8.0.0
- **New permission required:** "downloads":
    * Required to give the user the ability to backup their scoped rules to a file on their computer.
- Changes in _Rule manager_:
    * **Remove all** is now **Mark all for deletion**, whereas you now need to click _Commit all_ to confirm deleting all rules.
    * New button: **Reset to factory** = reset to out-of-the box rules.
    * New buttons: **Backup to file** and **Restore from file**, operate on the content of the _Recipe_ text area (so you can backup a single recipe or all of them).
        - **Restore from file** does not replace existing rules, it _adds_ on top of existing rules.
        - **Backup to file** requires a new permission for the extension ("Manage your downloads").
- Changes in extension popup:
    * The "preset recipes" button now has a badge showing the number of matching preset recipes.
    * A [button has been added](/gorhill/httpswitchboard/wiki/The-matrix-toolbar#wiki-remove-all-temporary-rules) to take over the task of removing all temporary rules.
    * The function of [the existing button](/gorhill/httpswitchboard/wiki/The-matrix-toolbar#wiki-remove-temporary-rules-from-current-scope) has changed to "revert temporary rules **for current scope**".
- More internal work on preset recipes (bringing the feature out of beta status is the goal).
    * File format is YAML-compliant. Benefits: future-proofing, syntax highlighting.
    * Internally, preset recipes can now be composite.
        - For example, "Google Groups with account" is a composite of "Google Groups" (to "unbreak" Google groups) and "Google Account" (to "unbreak" logging into your Google account.)
    * All 1st-party recipes are now scoped, and this will be the only accepted practice for 1st-party recipes.
- Updated all 3rd-party assets to their latest versions (preset blocked hosts, Public Suffix List).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/188>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/186>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/177>:
    * Thanks to [my-password-is-password](/my-password-is-password) for his [pull request](/gorhill/httpswitchboard/pull/180).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/186>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/176>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/175>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/174>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/166>.

***

- [Older change logs: 0.6.0.0 to 0.7.9.3](/gorhill/httpswitchboard/wiki/Change-log-0.6.0.0-to-0.7.9.3).
- [Even older change logs: 0.0.0.0 to 0.5.9.0](/gorhill/httpswitchboard/wiki/Change-log-0.0.0.0-to-0.5.9.0).