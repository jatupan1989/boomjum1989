_HTTP Switchboard_ uses the [chrome.webRequest API](http://developer.chrome.com/extensions/webRequest.html) to filter/report net requests. However, anything which is not passed to the above API by your Chromium-based browser can not be filtered/reported by HTTPSB.

These requests are not merely behind-the-scene (which are reported by HTTPSB), they are also unavailable to extensions, which means it is even more difficult for a user to be aware of these. So here are lists of all the connections which have been found to be hidden from user view, i.e. which can't even be reported as behind-the-scene requests by HTTPSB.

