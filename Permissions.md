HTTP Switchboard ("HTTPSB") requires the following permissions to work properly:

    "permissions": [
        "browsingData",
        "contentSettings",
        "contextMenus",
        "cookies",
        "downloads",
        "storage",
        "tabs",
        "unlimitedStorage",
        "webNavigation",
        "webRequest",
        "webRequestBlocking",
        "http://*/*",
        "https://*/*"
    ],

* [**browsingData**](http://developer.chrome.com/extensions/browsingData.html): to allow [clearing the browser cache](http://developer.chrome.com/extensions/browsingData.html#method-removeCache).
* [**contentSettings**](http://developer.chrome.com/extensions/contentSettings.html): to [enable javascript](http://developer.chrome.com/extensions/contentSettings.html#property-javascript) for all web pages so that the HTTPSB can fully control execution of javascript using the `Content-Security-Policy: script-src 'none'` header directive.
* [**contextMenus**](http://developer.chrome.com/extensions/contextMenus.html): to insert HTTPSB often-used commands in the context menu.
* [**cookies**](http://developer.chrome.com/extensions/cookies.html): to allow the removal of blocked cookies.
* [**downloads**](http://developer.chrome.com/extensions/downloads.html): to allow [backing up data to user-selected files](/gorhill/httpswitchboard/wiki/Change-log#wiki-0800).
* [**storage**](http://developer.chrome.com/extensions/storage.html): to store your own whitelist/blacklist domains/objects.
* [**tabs**](http://developer.chrome.com/extensions/tabs.html): to enable forcing a reload of the content of a tab (when the content of the whitelist/blacklist change).
* [**unlimitedStorage**](https://developers.google.com/chrome/whitepapers/storage#unlimited): to allow a user to update various assets used by HTTPSB (like preset blacklists, preset recipes, etc.) by fetching the latest versions from Github and saving them locally. Currently, HTTPSB limits itself to 24MB.
* [**webNavigation**](http://developer.chrome.com/extensions/webNavigation.html): to listen to [onBeforeNavigate](http://developer.chrome.com/extensions/webNavigation.html#event-onBeforeNavigate) events in order to set up HTTPSB's internal data structure for a specific web page.
* [**webRequest**](http://developer.chrome.com/extensions/webRequest.html): to allow intercepting all requests in order to inspect them.
* [**webRequestBlocking**](http://developer.chrome.com/extensions/webRequest.html#manifest): to be able to block a request if the object of the request is blacklisted.
* `http://*/*` & `https://*/*`: to be able to inspect HTTP net requests for all URLs (necessary in order to decide whether a block directive should be enforced).