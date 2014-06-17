[under construction: there is so much to cover..]

### Hyperlink auditing

I became aware about "hyperlink-auditing" after reading [this post](http://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/).

Reference: <http://www.whatwg.org/specs/web-apps/current-work/multipage/links.html#hyperlink-auditing>.

Starting with version 0.9.9.0, it is possible to block requests which purpose is to serve hyperlink-auditing information to whatever party. The default setting is to block all hyperlink-auditing requests -- as there are no benefit to the users to have their browsing activity tracked.

On the technical side, I have [observed](http://jsfiddle.net/Ronny/5ntzw/) that hyperlink-auditing requests are reported as request of type `other`, in the [behind-the-scene](/gorhill/httpswitchboard/wiki/Behind-the-scene-requests) matrix. So this means that hyperlink-auditing requests will be reported in the `other` column of the matrix, and may be reported on the matrix of the page where the request originate or in the behind-the-scene matrix if HTTPSB does not have enough information to bind the request to the page where it occurred.

**Note:** I verified that disabling the `chrome://flags/#disable-hyperlink-auditing` flag **does not** disable hyperlink-auditing. Do not rely on this setting.