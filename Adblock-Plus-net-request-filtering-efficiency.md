Adblock Plus net request filtering is based on finding pattern in a URL.

For example, the first filter in [EasyList](https://easylist.adblockplus.org/en/) is `&ad_box_`, which means: "If the URL of a net request contains the sub-string `&ad_box_` at any position, block the request".

Net filtering based on finding pattern in a URL is a CPU-intensive task, as for every request, a URL must be tested against thousands of pattern-based filters (over 20,000 just in EasyList, some with wildcard(s)), and this must be accomplish in real-time, in order to tell the browser whether the request should be allowed or cancelled.

In _HTTP Switchboard_, I eventually accepted to support Adblock Plus net request filters, after having [squarely refused](/gorhill/httpswitchboard/issues/149#issuecomment-32458730) to do so. Support for Adblock Plus net request filtering [first appeared in version 0.8.4.0](/gorhill/httpswitchboard/wiki/Change-log#0840).

When I decided to support pattern-matching net request filtering, I took the decision to start from scratch and to not look at ABP code on how they implemented pattern-matching net request filtering, and as with matrix filtering, the implementation had to be as efficient as possible.

ABP-compatible pattern-matching filters have been supported since a while now, but here I would like to show the difference in my implementation and that of the official ABP extension. Remember, pattern-matching a filter is a CPU-intensive operation, so the goal of an implementation is to minimize as much as possible the number of filters tested for each URL.

Here are the results for ADP first:

    ABP.adbProfiler> number or filters tested per URL: 107 (sample: 9600 URLs)
    ABP.adbProfiler> number or filters tested per URL: 107 (sample: 9800 URLs)
    ABP.adbProfiler> number or filters tested per URL: 108 (sample: 10000 URLs)
    ABP.adbProfiler> number or filters tested per URL: 108 (sample: 10200 URLs)
    ABP.adbProfiler> number or filters tested per URL: 109 (sample: 10400 URLs)
    ABP.adbProfiler> number or filters tested per URL: 108 (sample: 10600 URLs)
    ABP.adbProfiler> number or filters tested per URL: 108 (sample: 10800 URLs)
    ABP.adbProfiler> number or filters tested per URL: 107 (sample: 11000 URLs)
    ABP.adbProfiler> number or filters tested per URL: 106 (sample: 11200 URLs)
    ABP.adbProfiler> number or filters tested per URL: 107 (sample: 11400 URLs)

Then HTTPSB:

    HTTPSB.adbProfiler> number or filters tested per URL: 9 (sample: 9600 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 9800 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 10000 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 10200 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 10400 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 10600 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 10800 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 11000 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 11200 URLs)
    HTTPSB.adbProfiler> number or filters tested per URL: 8 (sample: 11400 URLs)
