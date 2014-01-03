When *HTTP Switchboard* is installed and active, if you look at *Chromium Settings*/*Privacy*/*Content settings*/*Javascript*/*Manage exceptions*, you will notice two entries (created by HTTPSB):

- `http://*    allow`
- `https://*   allow`

**Do not panic.**

HTTPSB uses a different and more reliable mechanism than other blockers on the Chromium platform to enforce the blocking of javascript. There are two ways in which javascript must be blocked:

- External javascript
- Inline javascript

For external javascript, this is trivial with the Chromium platform using the [webRequest API](http://developer.chrome.com/extensions/webRequest.html) to prevent the downloading of javascript files. If the file is not downloaded, obviously the javascript content can not be executed.

For inline javascript however, it is a bit more complicated.

Usually javascript blockers on the Chromium platform use (or try to) the [contentSettings API](http://developer.chrome.com/extensions/contentSettings.html), but this has proven challenging as the calls to create/delete rules in order to block javascript are not synchronous, meaning they take effect at some point in the future. This is problematic when it comes to block inline javascript.

To complicate the matter further, whether javascript is blocked or allowed in HTTPSB may depend on the scope of the rules (ex.: "allow javascript on `facebook.com` only when visiting `https://www.facebook.com`"), in which case the built-in whitelist/blacklist mechanism in Chromium just doesn't work.

