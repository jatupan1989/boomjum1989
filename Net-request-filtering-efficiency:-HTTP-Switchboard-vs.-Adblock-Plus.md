**Summary:** For a web page which requires fetching resources from 100 URLs (commonly above that nowadays on popular web sites), on average, _Adblock Plus_ ("ABP") will test 10,700 filters, while _HTTP Switchboard_ ("HTTPSB") will test 800 filters. Furthermore, the filter-testing javascript code is leaner and faster in HTTPSB than it is in ABP.

***

Adblock Plus net request filtering is based on finding pattern in a URL.

For example, the first filter in [EasyList](https://easylist.adblockplus.org/en/) is `&ad_box_`, which means: "If the URL of a net request contains the sub-string `&ad_box_`, at any position, block the request".

Net filtering based on finding pattern in a URL is a CPU-intensive task, as for every request, a URL must be (virtually) tested against thousands of pattern-based filters (over 25,000 when using EasyList + EasyPrivacy, some with wildcard(s) or other syntactic flavours), and this must be accomplished in real-time, in order to tell the (waiting) browser whether the request should be allowed or cancelled.

In _HTTP Switchboard_, I eventually accepted to support Adblock Plus net request filters, after having [squarely refused](/gorhill/httpswitchboard/issues/149#issuecomment-32458730) to do so. Support for Adblock Plus net request filtering [first appeared in version 0.8.4.0](/gorhill/httpswitchboard/wiki/Change-log#0840).

When I decided to support pattern-matching net request filtering, I took the decision to start from scratch and to not look at ABP code on how they implemented pattern-matching net request filtering -- in order to keep a "clean slate" mind. As with matrix filtering, the obvious goal for my implementation is that it had to be as efficient as possible.

ABP-compatible pattern-matching filters have been supported since a while now, but here I would like to show through benchmarking results the difference in my implementation and that of the official ABP extension. 

Remember, pattern-matching is a CPU-intensive operation, so the goal of an implementation is to minimize as much as possible the number of filters tested for each URL.

So for both ABP (v1.8.1/Chromium) and HTTPSB (0.9.5.1/Chromium), I ran my [reference benchmark](/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites), and here are the results. First, ADP:

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

In other words, as per results above:

HTTPSB is able to reduce the 25,000+ pattern-matching filters found in EasyList and EasyPrivacy into only eight tests for each URL (on average), while ABP is not able to reduce these same 25,000+ pattern-matching filters into less than 107 tests for each URL (on average).

How each filter is tested is also important: **it has to be fast**.

Here is the [filter test code in ABP](/adblockplus/adblockplus/blob/master/lib/filterClasses.js#L544) (note the regular expression):

    if (this.regexp.test(location) &&
        (RegExpFilter.typeMap[contentType] & this.contentType) != 0 &&
        (this.thirdParty == null || this.thirdParty == thirdParty) &&
        this.isActiveOnDomain(docDomain))
    {
      return true;
    }

    return false;

In HTTPSB, the test differs according to the filter type: at parse time, filters are categorized and an optimal representation is picked to store them, which means each filter is tested with optimal code.

For example, this is the test code for one of a very common filter (note that **no** regular expression is used):

    return url.substr(tokenBeg - 1, this.s.length) === this.s;

In HTTPSB, pattern-matching filtering is implemented with efficiency as the primary concern, and as a result HTTPSB is less likely to be a burden on the browser than ABP when loading web pages, especially those which are the results of hundreds of net requests.

Therefore, because of this better filtering efficiency in HTTPSB, I don't need to warn the user against using too many filters, [like ABP does here](https://adblockplus.org/en/getting_started#subscription) (excerpt, my emphasis):

> It is important to note that you should not add too many filterlists to Adblock Plus. **This will slow down the adblocker, therefore, your browsing.** As a rule of thumb, it is highly recommended to not use overlapping filterlists (e.g. choose either EasyList OR Fanboy's List).

HTTPSB's implementation of ABP-compatible net request filters is found in [js/abp-filters.js](/gorhill/httpswitchboard/blob/master/js/abp-filters.js).

I consider optimizing to be a never ending quest. Sometimes new ideas come to mind after we thought we got close to ultimate code optimization. Finding new ways to optimize further has happened many times for my implementation of ABP filters, so I won't be silly and claim it can't be improved :-)