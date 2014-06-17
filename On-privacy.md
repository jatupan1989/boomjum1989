[under construction: there is so much to cover..]

### Hyperlink auditing

I became aware about "hyperlink-auditing" after reading [this post](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/).

Reference: <http://www.whatwg.org/specs/web-apps/current-work/multipage/links.html#hyperlink-auditing>.

I have [observed](http://jsfiddle.net/Ronny/5ntzw/) that hyperlink-auditing pings are reported as requests of type `other`, in the [behind-the-scene](/gorhill/httpswitchboard/wiki/Behind-the-scene-requests) matrix. Be aware that HTTPSB ships with the behind-the-scene matrix- and ABP-filtering disabled in order to not break browser's auto-update features and to not interfere with other extensions.

Thus, privacy-conscious users will have to go to their behind-the-scene matrix and blacklist the `other` column in order to foil privacy-invading hyperlink-auditing.

You can access the behind-the-scene matrix by opening HTTPSB's dashboard: clicking the extension icon while in the dashboard will open the behind-the-scene matrix, from where matrix- and ABP-filtering can be turned on.

**Note:** I verified that disabling the flag `chrome://flags/#disable-hyperlink-auditing` **does not** disable hyperlink-auditing. Do not rely on this setting.