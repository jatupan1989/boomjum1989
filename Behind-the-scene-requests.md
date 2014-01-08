*HTTP Switchboard* ("HTTPSB") uses the [webRequest Chrome API](http://developer.chrome.com/extensions/webRequest.html) to inspect and filter requests made by your Chromium-based browser.

Whenever a request is made, the browser will pass the request to HTTPSB and wait for the extension to answer whether the request should blocked or not. Each request the browser passes to HTTPSB has a tab id value  which let an extension know from which tab opened in the browser the request originate.

Sometimes the tab id value is such that it tells the extension that the request originated from no opened tab. HTTPSB calls these requests "behind-the-scene" requests, since they cannot be bound to any particular web pages.



