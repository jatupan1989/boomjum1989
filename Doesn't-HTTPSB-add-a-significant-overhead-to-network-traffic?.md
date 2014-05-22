[The results in this article were out-dated. Anything in here is quite probably no longer reproducible. Some code might have gotten better, some other might have gotten worst. For instance, HTTPSB average time for its onBeforeRequest() has gone up, because it now handles ABP pattern-based filters. Other extensions might have improved or worsened. These numbers are no longer useful.]

TL;DR: No.

HTTPSB uses Chromium's [webRequest API](http://developer.chrome.com/extensions/webRequest.html) (more specifically, the `webRequest.onBeforeRequest` handler), which means for every single request, javascript code is executed in order to evaluate whether the request should be allowed or blocked.

Doesn't this javascript code add a significant overhead and slows down the download of web pages?

No.

A top priority task in this project is to ensure top performance for this part of the code. Currently, my profiling  shows that on average the overhead added to each request is less than 1/10 of a millisecond. I've tested other blockers out there, and I have seen some add as much as 30 ms per request on average (one was reading from `localStorage` for every request.)

For reference, I also measured the overhead added in the `webRequest.onBeforeRequest` handler of other popular blockers, AdBlock, Ghostery and Disconnect, and here are the results:

| Extension  | `webRequest.onBeforeRequest` avg time |
| ---------- |:-------------------------------------:|
| AdBlock    | 0.210 ms                              |
| Disconnect | 0.270 ms                              |
| Ghostery   | 3.000 ms                              |
| HTTPSB     | 0.100 ms                              |

This is for the critical request handling code, this doesn't include the lower priority code (i.e. updating extension icon, content scripts, etc.). (In HTTPSB this lower priority handling code is minimal as HTTPSB doesn't modify the content of web page -- I don't know about other blockers.)

Now to understand how these overheads can affect the loading of a web page, for example imagine a web page with 300 internal requests (not uncommon nowadays: front page of wired.com is over 300 requests), so the total average overhead would be 300 x `webRequest.onBeforeRequest` avg time, meaning a cumulative overhead of ...

*  63 ms for AdBlock
*  81 ms for Disconnect
* 900 ms for Ghostery
*  30 ms for HTTPSB.