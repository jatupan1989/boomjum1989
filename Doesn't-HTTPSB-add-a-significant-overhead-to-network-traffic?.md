HTTPSB used Chromium's [webRequest API](http://developer.chrome.com/extensions/webRequest.html), which means for every single request, javascript code is executed in order to evaluate whether the request should be allowed or blocked.

Doesn't this javascript code add a significant overhead and slows down the download of web pages?

No.

A top priority task in this project is to ensure performance of this part of the code. Currently, my profiling  shows that on average the overhead added to each request is less than 1/10 of a millisecond. I've tested other blockers out there, and I have seen some add as much as 30 ms per request on average..