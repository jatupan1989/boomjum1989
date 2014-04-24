**TL;DR I can't guarantee HTTPSB will run flawlessly on a development version of a Chromium-based browser.**

I develop and test HTTPSB using the latest official releases of Chromium (v33/Linux), Chrome (v34/Linux&Windows) and Opera (v20/Windows). Once in a while I test the official release of Yandex (it has been a while though). I guess I should set-up a development version of Chromium, but I do not have much time currently to do so.

I know it often happens people report that HTTPSB has some malfunctions with a development version of one of the Chromium-based browsers, malfunctions which I often can't reproduce on an official release.

### Compatibility with other extensions

I will list here known issues, benign or serious, with other extensions.

### Any extension which modifies request and/or response headers

**NOT COMPATIBLE.**

Chrome API allows [only **ONE** extension to modify request or response headers](https://developer.chrome.com/extensions/webRequest#implementation), and the last one installed wins.

Since modifying request and response headers is **key** for _HTTP Switchboard_ to perform its duty reliably (disabling javascript execution, stripping outgoing cookies, referer, etc.), consider that any extension which requires modifying HTTP headers is strictly incompatible with _HTTP Switchboard_: One of the two extensions won't be able to do its job, which in the case of HTTPSB is critical.

### [Adblock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb)

Both extensions may try to replace the content of `<iframe>` objects with harmless content using a redirect operation. When this happens, the browser will warn of a conflict.

### [ScriptSafe](https://chrome.google.com/webstore/detail/scriptsafe/oiigbmnaadbkfbmpbfijlflahbdbdgdf)

ScriptSafe doesn't work properly with HTTPSB when scripts are blocked by HTTPSB.

HTTPSB blocks javascript execution using a [Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy) directive (ScriptSafe uses [chrome.contentSettings.javascript.set](https://developer.chrome.com/extensions/contentSettings#property-javascript).)

The use of a Content Security Policy by HTTPSB prevents script files from even being requested, and as a result [chrome.webRequest.OnBeforeRequest](https://developer.chrome.com/extensions/webRequest#event-onBeforeRequest) is not fired for these external files, which causes ScriptSafe to not see the existence of these files, therefore they won't appears in ScriptSafe user interface, therefore they can't be whitelisted.

Allowing 1st-party scripts in HTTPSB causes ScriptSafe to be able to see external scripts.

My advice is to stick to one extension or the other, and not have both installed and enabled at the same time.

