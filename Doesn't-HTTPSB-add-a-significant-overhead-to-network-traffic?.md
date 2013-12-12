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
| HTTPSB     | 0.090 ms                              |

This is for the critical request handling code, this doesn't include the lower priority code (i.e. updating extension icon, content scripts, etc.). (In HTTPSB this lower priority handling code is minimal as HTTPSB doesn't modify the content of web page -- I don't know about other blockers.)

Now to understand how these overheads can affect the loading of a web page, for exemple imagine a web page with 100 internal requests (commonly above that nowadays), so the total average overhead would be 100 x `webRequest.onBeforeRequest` avg time, meaning 21 ms for AdBlock, 27 ms for Disconnect, 300 ms for Ghostery, and 9 ms for HTTPSB.