*HTTP Switchboard* ("HTTPSB") uses the [webRequest Chrome API](http://developer.chrome.com/extensions/webRequest.html) to inspect and filter requests made by your Chromium-based browser.

Whenever a request is made, the browser will pass the request to HTTPSB and wait for the extension to answer whether the request should be blocked or not. Each request the browser passes to HTTPSB has a tab id value  which let an extension know from which tab opened in the browser the request originate.

Sometimes the tab id value is such that it tells the extension that the request originated from no opened tab. HTTPSB calls these requests "behind-the-scene" requests, since they cannot be bound to any particular web pages.

Now these behind-the-scene requests **may** actually be related to one of the opened tab, but for some reasons the browser didn't give this information. For example, it is my experience on Chromium that requests for [favicon](http://en.wikipedia.org/wiki/Favicon) objects are made and no tab id information is provided for these requests, which means HTTPSB has no choice but to report these requests as being behind-the-scene requests, even though they are obviously related to one of the web pages opened in one of the tabs.

So regarding behind-the-scene requests, the following statement is very important before you make any conclusion on a particular behind-the-scene request you encounter:

**Behind-the-scene requests may or may not actually be related to one of the URL addresses appearing in one of the opened tabs.**

So if after thorough investigation you really can't associate a particular behind-the-scene request with one of the URL addresses of one of the opened tabs, then you probably made a convincing case that the particular behind-the-scene request was really expressly made by the browser behind the scene.
