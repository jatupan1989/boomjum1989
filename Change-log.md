For conciseness, *HTTP Switchboard* is referred as HTTPSB in the text below. This page is often updated **before** the latest version is released.

### 0.8.8.0
- Not released yet.
- New option in the _Settings_ tab: "Auto delete unused temporary scopes".
    * Disabled by default.
    * Especially useful for users who have enabled "Auto create temporary site-level scopes".
    * A temporary scope (which has no permanent counterpart) won't be deleted _immediately_ after the web page for which it applies is closed. It will linger a bit, and if it still unused after 20 minutes or so, it will be removed from memory.

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

### 0.7.9.3
- Opera requires that Youtube works out-of-the-box:
    * A site-level scope for Youtube is created at _install_ time.
    * I decided to do this for all flavors of Chromium, not just Opera.
- Small improvements to the _Remove all_ function in _Rule manager_:
    * No longer remove whitelisting of `css` and `image` rules in global scope (if they exist): that was a bit radical (users who really want these gone are just two clicks away at most from literally removing all rules.)
    * Scopes are completely flushed from memory. They used to hang around ready to be brought back to life, which is nice when playing with the scope menu in the popup, but not nice when user expects a clean slate after using _Remove all_.
        - This was most confusing for users who checked the _Auto create temporary site-level scope_ option.
- So mainly this version was to pass Opera store review process (Youtube must work at first install), I don't plan to release this one to the Chrome store, as I want to wait for a fix to [issue #166](/gorhill/httpswitchboard/issues/166).

***

### 0.7.9.2
- **Emergency fix**: Due to latest changes regarding scopes, a portion of code which was not revised caused HTTPSB to fall into allow-all/block-exceptionally mode.
    * More technically, that piece of code was to whitelist all requests from behind-the-scene scope if the scope was not found. With latest changes, the behind-the-scene scope was indeed never found, and because of this the whitelist-all default rule for behind-the-scene scope was created in the global scope.
- **If you were working in [block-all/allow-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-block-allallow-exceptionally-approach), please do click the "all" matrix cell to toggle it back to red** (if ever it is now green as in [allow-all/block-exceptionally mode](/gorhill/httpswitchboard/wiki/How-to-use-HTTP-Switchboard:-Two-opposing-views#wiki-the-allow-allblock-exceptionally-approach)), **and lock the change.**
    * Also, you may want to check your [behind-the-scene matrix](/gorhill/httpswitchboard/wiki/Behind-the-scene-requests): Out-of-the-box, this matrix is in allow-all/block-exceptionally mode, so as to not interfere with the browser operation and other installed extensions. If you never changed the behind-the-scene matrix from its out-of-the-box default and you find that it is currently in block-all/allow-exceptionally mode, reset it to its original state by clicking the "all" matrix cell to turn it green, than lock the matrix.
- Sorry. The changes re. scopes was a big change, and I failed to revise this one portion of code.

***

### 0.7.9.1
- More 1st- and 3rd-party [preset recipes](/gorhill/httpswitchboard/blob/master/assets/httpsb/presets.txt) added.
    * While at it, I made the preset recipes popup sticky, i.e. user can click multiple preset recipes without the popup closing after clicking on a single preset.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/172>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/171>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/160>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/157>:
    * The storage usage can now be seen in the _Statistics_ page, at the top.

***

### 0.7.9.0
- **Important change**: The scheme (or "protocol") is now ignored in a scope definition. A scope is now defined solely by its hostname for site-level scopes or domain name for domain-level scopes. For example, a scope for `www.example.com` will no longer be defined as `http://www.example.com` or `https://www.example.com`, but just by `www.example.com`, i.e. the scheme is ignored. Having two flavors for the same site- or domain-level scope was just confusing and unmanageable for the users (it was for me, so imagine for users), and was actually broken in the UI itself.
    - This takes care of [issue #165](/gorhill/httpswitchboard/issues/165).
    - The transition from old scopes to new scopes is all taken care.
    - If you want to enforce `https` vs `http`, I recommend installing [HTTPS Everywhere](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp).
- Added a few more preset recipes:
    * Brightcove as 3rd-party.
    * Instagram as 3rd-party.
    * Vine as 3rd-party.
    * Huffington Post as 1st-party.
    * Youtube as 1st-party (no login yet though, will work on this).
- Fixed <https://github.com/gorhill/httpswitchboard/issues/170>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/169>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/168>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/165>.

***

### 0.7.8.0
- **New feature** (beta): Preset recipes available from the popup menu. HTTPSB will display all relevant recipes given the state of the matrix. Clicking on a recipe will import its rules in order to enable a specific feature on a web page:
    * ![Preset recipes](https://raw2.github.com/gorhill/httpswitchboard/master/doc/img/httpsb-preset-recipes-generic-1.png)
    * For example, for a web page with an embedded -- but blocked -- Youtube video, the popup will offer the import of a "Youtube" recipe which should enable the embedded video to play properly.
    * Consider this feature beta.
    * There are very few preset recipes for now but I do hope more will be contributed by the community, for the benefit of the community.
        - Pull requests for useful recipes will be greatly appreciated.
        - I will soon provide here a link to a wiki page which describe the syntax.
    * Currently, only recipes available: Youtube, Vimeo, Disqus, Livefyre (as 3d parties).
    * I will work to add more useful recipes and make quick minor updates in the coming days to make these available.
    * It is a convenient feature for everybody, but primary motivation is to help less advanced user to not give up on the extension.
- Added new preset lists of blocked hosts:
    * [Adblock+ EasyList](https://easylist-downloads.adblockplus.org/easylist.txt)
    * [Adblock+ EasyPrivacy](https://easylist-downloads.adblockplus.org/easyprivacy.txt)
    * [Fanboy's Annoyance List](https://easylist-downloads.adblockplus.org/fanboy-annoyance.txt)
    * [Fanboy's Enhanced Tracking List](http://www.fanboy.co.nz/enhancedstats.txt)
    * **Important note:** HTTPSB extracts and uses **ONLY** filters which correspond to blocking an entire domain from the Adblock-filter lists, since HTTPSB doesn't support finer granularity beyond `type of request`/`hostname`.
    * Added [block-facebook.txt](https://github.com/gorhill/httpswitchboard/blob/master/assets/httpsb/block-facebook.txt) for those who do not want Facebook to have the ability to track them.
        - Since preset blocked hosts are omnipresent (they are seen by all scopes), it is more convenient and efficient to block Facebook using such a preset list.
- In the _Settings_ page, for each preset lists in use, HTTPSB now displays the number of entries used and the total number of entries present. Less entries might be shown as "used" because of duplicate entries in two or more lists.

***

### 0.7.7.1
- Added `aad73c550c.se` to [httpsb-blacklist.txt](/gorhill/httpswitchboard/blob/f92b98cccd3b7f3278d3e6a59b5be48f45f2fb21/assets/httpsb-blacklist.txt): Related to `adrotator.se`
- Fixed <https://github.com/gorhill/httpswitchboard/issues/163>.
- Fixed <https://github.com/gorhill/httpswitchboard/issues/162>.

***

### 0.7.7.0

- URL redirections are now reported in the matrix of the landing page.
    * URL redirections are recognizabled by a group of domain/subdomains in the matrix for which all the cells are empty. [More details re. URL redirections](https://github.com/gorhill/httpswitchboard/wiki/URL-redirections).
- Added `panoramtech.net` to HTTPSB's list of blocked hosts.
    * Because it is in the screenshot used in this article: [Adware vendors buy Chrome Extensions to send ad- and malware-filled updates](http://arstechnica.com/security/2014/01/malware-vendors-buy-chrome-extensions-to-send-adware-filled-updates/). 
- Fixed <https://github.com/gorhill/httpswitchboard/issues/158>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/150>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/148>
- Fixed <https://github.com/gorhill/httpswitchboard/issues/139>
    * Chromium-behind-the-scene scope has its own section in the *Rule manager* page.
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

[Older change logs](https://github.com/gorhill/httpswitchboard/wiki/Change-log-0.0-to-0.5).