*HTTP Switchboard* ("HTTPSB") uses the [webRequest Chrome API](http://developer.chrome.com/extensions/webRequest.html) to inspect and filter requests made by your Chromium-based browser.

Whenever a request is made, the browser will pass the request to HTTPSB and wait for the extension to answer whether the request should be blocked or not. Each request the browser hands over to HTTPSB has a tab id value, which id lets an extension know from which tab opened in the browser the request originates.

Sometimes the tab id value is such that it tells the extension that the request originated from no opened tab. HTTPSB calls these requests "behind-the-scene" requests, since they cannot be bound to any particular web pages.

Now these behind-the-scene requests **may** actually be related to one of the opened tab, but for some reasons the browser didn't give this information. For example, it is my experience on Chromium that requests for [favicon](http://en.wikipedia.org/wiki/Favicon) objects are often made with no tab id information, which means HTTPSB has no choice but to report these requests as being behind-the-scene requests, even though a human would be able to understand they are obviously related to one of the web pages opened in one of the tabs.

So regarding behind-the-scene requests, the following statement is very important before you make any conclusion on a particular behind-the-scene request you encounter:

**Behind-the-scene requests may or may not be actually related to one of the URL addresses appearing in one of the opened tabs.**

So if after thorough investigation you really can't associate a particular behind-the-scene request with one of the URL addresses of one of the opened tabs, then you probably made a convincing case that the particular behind-the-scene request was really expressly made by the browser behind the scene, **or** by one of the extensions installed in the browser.

Keep this caveat in mind when you draw conclusions based on what HTTPSB reports as behind-the-scene requests.

You can access the matrix for behind-the-scene requests by clicking the extension icon while on HTTPSB's dashboard:

![Matrix example for behind-the-scene requests](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/behind-the-scene-matrix-generic-example-1.gif "You choose what to block or not to block: Nothing, all, or anything else in between")

You can completely choose how behind-the-scene requests are filtered: allow all by default, block all by default, or selectively allow/block as per your choices.

Out of the box, the matrix for behind-the-scene requests is in allow-all mode, in order to ensure there is no interference with the default behavior of the browser or installed extensions.

From there you can choose to block selectively or wholly, while keeping in mind that Chromium-based browsers may use behind-the-scene requests in the course of their normal operation, and also keep in mind extensions may also perform their own net requests which appear as behind-the-scene requests to HTTPSB.

If you choose to block wholly or partially behind-the-scene requests, you are responsible for any potentially negative side-effects. For example, if you block requests which are used by the browser to update or install extensions, please don't blame HTTPSB for actually preventing the update or installation of extensions.