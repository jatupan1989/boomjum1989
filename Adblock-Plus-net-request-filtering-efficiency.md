Adblock Plus net request filtering is based on finding pattern in a URL.

For example, the first filter in [EasyList](https://easylist.adblockplus.org/en/) is `&ad_box_`, which means: "If the URL of a net request contains the sub-string `&ad_box_`, block the request".

Net filtering based on finding pattern in a URL is a CPU intensive task, as for every request, a URL must be tested against thousands of pattern-based filters (over 20,000 just in EasyList), and this must be accomplish in real-time, in order to tell the browser whether the request should be allowed or cancelled.

In _HTTP Switchboard_, I eventually accepted to support Adblock Plus net request filters, after having squarely refused to do so. Support for Adblock Plus net request filtering [first appeared in version 0.8.4.0](https://github.com/gorhill/httpswitchboard/wiki/Change-log#0840).