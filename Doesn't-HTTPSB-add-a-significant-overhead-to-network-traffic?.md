HTTPSB uses Chromium's [webRequest API](http://developer.chrome.com/extensions/webRequest.html) (more specifically, the `webRequest.onBeforeRequest` handler), which means for every single request, javascript code is executed in order to evaluate whether the request should be allowed or blocked.

Doesn't this javascript code add a significant overhead and slow down the download of web pages?

No.

A top priority task in this project is to ensure top performance for this part of the code. Currently, my profiling  shows that on average the overhead added to each request is less than 1/10 of a millisecond. I've tested other blockers out there, and I have seen some add as much as 30 ms per request on average (one was reading from `localStorage` for every request.)

For reference, I also measured the overhead added in `webRequest.onBeforeRequest` handler by two other popular blockers, Ghostery and Disconnect, and here are the results:

| Extension  | `webRequest.onBeforeRequest`: avg time |
| ---------- |:--------------------------------------:|
| Disconnect | 0.270 ms                              :|
| Ghostery   | 3.000 ms                              :|
| HTTPSB     | 0.090 ms                              :|

This is for the critical request handling code, this doesn't include the lower priority code (i.e. updating extension icon, content scripts, etc.). Now to understand how these overhead can affect the loading of a web page, for exemple imagine a web page with 100 internal requests (commonly above that nowadays), so the total average overhead would be 100 x `avg measured overhead`, 27 ms for Disconnect, 300 ms for Ghostery, and 9 ms for HTTPSB.