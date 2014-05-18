Many people have asked me to support ABP element hiding filters (I prefer to refer to these as "cosmetic filters") in the past. I've always resisted because I see _HTTP Switchboard_ as a tool to inform/manage where your browser connects. So...

Regarding [ABP memory consumption](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/), I'm with Firefox about this.

When the way to implement ABP element hiding filters is to inject a [gigantic style sheet](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/comment-page-1/#comment-11173) in every page (and frame), it bothers me to see the blame shifted onto Firefox.

Injecting such a large number of CSS rules indiscriminately is nonsense, and this is the **first** thing which should be addressed before asking Firefox to fix itself.

This is what motivated me to actually support ABP cosmetic filters: it's easier to demonstrate that clearly the code can be improved rather than talk about it endlessly. So here it is, with version 0.9.4.0, ABP cosmetic filters are supported.

Consider this feature early beta, and as of writing, the support is somewhere around 87% of all cosmetic filters (there is no performance issue or otherwise in supporting the missing filters, it's just a time thing). Note that I didn't spent that much time trying to optimize further than the primary proof-of-concept to show it is possible to improve memory consumption in ABP.

Here is a first test to compare memory consumption when loading this page in the browser:

![Memory: ABP vs HTTPSB](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/abp-vs-httpsb-mem-test1.png)

Note that in the test above, HTTPSB had its default out-of-the-box preset blocked hosts loaded and enabled in the matrix filtering engine, which represents an extra 60,000 filter rules, something not present in ABP.