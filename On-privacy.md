[under construction: there is so much to cover..]

### Hyperlink auditing

Reference: <http://www.whatwg.org/specs/web-apps/current-work/multipage/links.html#hyperlink-auditing>.

I have [observed](http://jsfiddle.net/Ronny/5ntzw/) that hyperlink-auditing pings are reported as a request of type `other`, in the [behind-the-scene](/gorhill/httpswitchboard/wiki/Behind-the-scene-requests) matrix. Be aware that HTTPSB ships with the behind-the-scene matrix in allow-all mode in order to not break browser's auto-update features and to not interfere with other extensions.

Thus, privacy-conscious users will have to go to their behind-the-scene matrix and blacklist the `other` column in order to foil privacy-invading hyperlink-auditing.