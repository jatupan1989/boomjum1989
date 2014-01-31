HTTP Switchboard ("HTTPSB") requires the following permissions to work properly:

    "permissions": [
        "browsingData",
        "contentSettings",
        "cookies",
        "downloads",
        "storage",
        "tabs",
        "webNavigation",
        "webRequest",
        "webRequestBlocking",
        "http://*/*",
        "https://*/*"
    ],

* **browsingData**: to allow [clearing the browser cache](http://developer.chrome.com/extensions/browsingData.html#method-removeCache).
* **contentSettings**: to [enable javascript](http://developer.chrome.com/extensions/contentSettings.html#property-javascript) for all web pages so that the HTTPSB can fully control execution of javascript using the `Content-Security-Policy: script-src 'none'` header directive.
* **contextMenu**: to insert HTTPSB often-used commands in the context menu.
* **cookies**: to allow the removal of blocked cookies.
* [**downloads**](http://developer.chrome.com/extensions/downloads.html): to allow backing up of data to user-selected files.
* **storage**: to store your own whitelist/blacklist domains/objects.
* **tabs**: to enable forcing a reload of the content of a tab (when the content of the whitelist/blacklist change), and to enable [injecting code](https://github.com/gorhill/httpswitchboard/blob/master/js/inject.js) into a page which reports all `<script>`, `<object>` and `<embed>` tags used on the page.
* **webNavigation**: to listen to [onBeforeNavigate](http://developer.chrome.com/extensions/webNavigation.html#event-onBeforeNavigate) events in order to set up HTTPSB's internal data structure for a specific web page.
* **webRequest**: to allow intercepting all requests in order to inspect them.
* **webRequestBlocking**: to be able to block a request if the object of the request is blacklisted.
* `http://*/*` & `https://*/*`: to be able to inspect HTTP net requests for all URLs (necessary in order to decide whether a block directive should be enforced).