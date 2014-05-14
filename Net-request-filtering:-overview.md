<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-overview.png" />
</p>

The matrix filtering engine and the ABP filtering engine can be selectively turned on or off, independently. Whether matrix filtering and/or ABP filtering is on or off is a per-scope setting. When both filtering engines are turned off, HTTPSB can still be useful by acting as a reporting tool, as it will still report in the matrix and request log all the net connections a web page does.

Great care has been taken to write CPU- and memory-efficient code for both filtering engines.

## Matrix filtering

Matrix filtering uses a inheritance model to transfer the block or allow status of a node to a lower precedence node:

<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-mtxfiltering-overview.png" />
</p>

Where _type_ correspond to the type of the request, which currently can be: _cookie_, _stylesheet_/_web font_, _image_, _plug-in_, _script_, _xmlhttprequest_, _iframe_, and _other_ (HTML5 video, HTML audio, SVG, and some other uncategorized requests).
To use a concrete example, let's take the following URL: `https://www.example.com/image.png`.

The hostname and the type of the request is extracted from the URL:

- Hostname: `www.example.com`
- Type: `image`

To evaluate whether the request should be blocked or allowed, matrix filtering will first look-up the block/allow status using exactly the hostname and type, then go up the hierarchy for when no explicit rule is found:

- Is `image` from `www.example.com` whitelisted?
- Yes: request is allowed
- No: Is `image` from `www.example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is `image` from `example.com` whitelisted?
- Yes: request is allowed
- No: Is `image` from `example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is everything from `example.com` whitelisted?
- Yes: request is allowed
- No: Is everything from `example.com` blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is `image` from anywhere whitelisted?
- Yes: request is allowed
- No: Is `image` from anywhere blacklisted?
- Yes: request is blocked
- No: Go up one step in the precedence hierarchy
- Is everything from anywhere whitelisted?
- Yes: request is allowed
- No: Is everything from anywhere blacklisted?
- Yes: request is blocked
- No: request is blocked

Actually, things are a bit more complicated, as the pseudo-code above doesn't take into account that type/domain (or type/subdomain) nodes inherit from two ancestors. HTTPSB deals with the ambiguity by allowing such requests **if and only if** both ancestor nodes evaluate as "allowed". However, if [strict blocking](/gorhill/httpswitchboard/wiki/%22Strict-blocking%22-illustrated) is disabled, the status of the domain (or subdomain) ancestor node has precedence over the type ancestor node.

The hierarchical evaluation in matrix filtering allows a user to easily toggle whole set of block/allow permissions by just blacklisting or whitelisting a single node. For instance, whitelisting (or blacklisting) the "all" node allows to turn all graylisted descendant nodes into allow (or block) mode.

All requests are evaluated in real-time against the current state of the matrix, so this means even future requests which have not been seen yet are affected by any change made to the matrix. For instance, this address a [problem often raised by NoScript users](http://forums.informaction.com/viewtopic.php?f=7&t=8309): with HTTPSB, if a user whitelists (or blacklists) the `all` cell in the matrix, all graylisted descendant cells will inherit the _allow_ (or _block_) status of the `all` cell.

Note that matrix filtering is used to evaluate more than just whether net requests are to be allowed or blocked. It is also used to evaluate:

- Whether javascript execution should be blocked
- Whether cookies should be stripped from outgoing HTTP headers
- Whether HTTP referer information should be stripped from outgoing HTTP headers
- Whether HTML5 localStorage should be emptied for a particular hostname

## ABP filtering

Starting with [version 0.8.4.0](https://github.com/gorhill/httpswitchboard/wiki/Change-log#0840), HTTPSB supports the parsing and enforcing ABP filter syntax.

ABP filters allow for a more granular control than matrix filtering when it comes to block net requests, as it is based on finding patterns in the whole URL, rather than just looking at the hostname and type of a net request.

Only filters which purpose is to block net requests are supported. Element hiding filters and filters with the `$popup` option are ignored, since HTTPSB's primary purpose is to control net requests.

With version 0.9.2.0, the proportion of parsed and enforced net request-related ABP filters is 99.7% of all net request-related ABP filters.

ABP filtering takes place **after** matrix filtering, therefore if a specific net request is blocked through matrix filtering, then ABP filtering will not be used, as the net request has already been evaluated as blocked.

Any net request which is evaluated as "allowed" by matrix filtering will however be further evaluated through the ABP filtering engine.

Great care has been taken to implement an efficient ABP filtering engine in HTTPSB (code was written from scratch), and the result is such that it consumes considerably less memory and CPU cycles than the official ABP extension on Chromium-based browsers.

To give a glimpse of the better performance of HTTPSB over ABP in handling ABP-compatible filters, I measured that on average, **ABP evaluates 121 filters/URL**, while for the same benchmark **HTTPSB evaluates 5 filters/URL**.<sup>[1]</sup>

Also, whereas ABP uses regular expressions internally to test for a filter match, HTTPSB uses simpler plain string comparisons whenever it is more efficient to do so, which is true for the great majority of filters (see <http://jsperf.com/regexp-vs-indexof-abp-miss/3> and <http://jsperf.com/regexp-vs-indexof-abp-hit/3>).

<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/abp-vs-httpsb.png" /><br>
    <sup>Memory footprint<br>(both matrix and ABP filtering were enabled in HTTPSB)</sup>
</p>

In the above screenshot, Adblock Plus 1.7.4, Adblock 2.6.28, and HTTPSB 0.8.9.2 were set to use [_EasyList without element hiding_](https://easylist-downloads.adblockplus.org/easylist_noelemhide.txt) and [_EasyPrivacy_](https://easylist-downloads.adblockplus.org/easyprivacy.txt). So-called "acceptable ads" was disabled in ABP.

<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/onbeforerequest-perf.png" /><br>
    <sup>CPU footprint: Average time spent to process each single net request: ABP vs. HTTPSB<br>(both matrix and ABP filtering were enabled in HTTPSB)</sup>
</p>

**Now regarding the above results, an important fact:** HTTPSB was using **an extra 56,000+ blocked hosts** as matrix-filtering rules (those rules are enabled out-of-the-box), and yet despite this, HTTPSB runs much leaner and faster than ABP, as seen above.<sup>[2]</sup>

The test was run on Google Chrome 34 for Linux, on Linux Mint 16 64-bit. The benchmark was the same as the one used in ["Comparative benchmarks against widely used blockers: Top 15 Most Popular News Websites"](https://github.com/gorhill/httpswitchboard/wiki/Comparative-benchmarks-against-widely-used-blockers:-Top-15-Most-Popular-News-Websites) (except `repeat` was set to 2), then all the tabs were closed (except for the _Extensions_ tab), and the browser was left idling for over 20 minutes to ensure the browser's garbage collector cleared unused memory from the extensions. The extensions were benchmarked alone, with no other extension present.

***

[1] For this particular measurement, the result in the case of HTTPSB was a _worst-case scenario_, as matrix filtering had been turned off so as to ensure apples-vs-apples comparison: no requests were blocked by the matrix filtering engine, therefore all filtering duty fell onto the ABP filtering engine.

[2] I still have an extra improvement in store to further reduce memory footprint regarding the implementation of ABP filters, but I do not consider this a priority at this point.