Many people have asked me to support ABP element hiding filters (I prefer to refer to these as "cosmetic filters") in the past. I've always resisted because I see _HTTP Switchboard_ as a tool to inform/manage where your browser connects. So...

Regarding [ABP memory consumption](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/), I'm with Firefox about this.

When the way to implement ABP element hiding filters is to inject a [gigantic style sheet](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/comment-page-1/#comment-11173) in every page (and frame), it bothers me to see the blame shifted onto Firefox.

Injecting such a large number of CSS rules indiscriminately is nonsense, and this is the **first** thing which should be addressed before asking Firefox to fix itself.

This is what motivated me to actually support ABP cosmetic filters: it's easier to demonstrate that clearly the code can be improved. So here it is, with [version 0.9.4.0](/gorhill/httpswitchboard/wiki/Change-log#0940), ABP cosmetic filters are supported.

The major difference with ABP implementation is that only the CSS rules which are relevant to a page are injected, which means a handful of them at most for a typical ad-driven web page, and often none at all -- as opposed to ABP which injects 20,000 CSS rules into every single web page ([as per ABP developer](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/comment-page-1/#comment-11173)). For example, visiting [www.wired.com](http://www.wired.com/) with matrix filtering turned off, only **one single CSS rule** is injected into the page by HTTPSB.

Consider this feature early beta, and as of writing, the support is somewhere around 87% of all cosmetic filters (there is no performance issue or otherwise in supporting the missing filters, it's just a time thing). Note that I didn't spent that much time trying to optimize further than the primary proof-of-concept to show it is possible to improve memory consumption, and improve how fast web pages come to live (not injecting 20,000 CSS rules has a noticeable effect on how fast pages are parsed by the browser).

Here is a first test to compare memory consumption when loading [this page](http://vimcolorschemetest.googlecode.com/svn/html/index-c.html) in the browser:

![Memory: ABP vs HTTPSB](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/abp-vs-httpsb-mem-test1.png)

Note that in the test above, HTTPSB had its default out-of-the-box preset blocked hosts loaded and enabled in the matrix filtering engine, which represents an extra 60,000 filter rules, something not present in ABP. Also, HTTPSB injects two more scripts into every pages and frames as part of its normal operation, these add up too, so the memory footprint could be even (quite I suspect) lower if it wasn't for these two extra content scripts.

Tests for screenshots above was Chromium 34 on Linux 64-bit.

Implementation ([abp-hide-filters.js](/gorhill/httpswitchboard/blob/master/js/abp-hide-filters.js)) is rather modular, it doesn't really depend on anything else in HTTPSB except for the utility to extract domain name from a URL, which should be easy enough to replace.