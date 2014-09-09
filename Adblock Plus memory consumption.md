**Summary:** Where _Adblock Plus_ ("ABP") indiscriminately injects over 13,000 generic CSS rules into every page and frames, _HTTP Switchboard_ ("HTTPSB") injects only a handful generic CSS rules at most. HTTPSB's approach is to perform a quick web page survey in order to dramatically narrow down the generic CSS selectors which need to be injected in web pages and frames. Examples: on [wired.com](http://www.wired.com/) ABP injects over 13,000 generic CSS selectors while **HTTPSB injects only 8 generic CSS selectors**; and on a page with no ads, ABP still injects over 13,000 generic CSS selectors while **HTTPSB injects none**.

***

Many people have asked me to support ABP element hiding filters (I prefer to refer to these as "cosmetic filters") in the past. I've always resisted because I see _HTTP Switchboard_ as a tool to inform/manage where your browser connects. But...

Regarding [ABP memory consumption](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/), I'm with Firefox on this.

When the way to implement ABP element hiding filters is to inject a [gigantic style sheet](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/comment-page-1/#comment-11173) in every page (and frame), it bothers me to see the blame shifted onto Firefox.

Injecting such a large number of CSS rules indiscriminately is nonsense, and this is the **first** thing which I thought should be addressed before asking Firefox to fix itself.

This is what motivated me to actually support ABP cosmetic filters: it's easier to demonstrate that the code can be improved by actually writing it. So here it is, with [version 0.9.4.0](/gorhill/httpswitchboard/wiki/Change-log#0940), ABP cosmetic filters are supported.

The major difference with ABP implementation is that only the CSS rules which are relevant to a page are injected, which means a handful of them at most for a typical ad-driven web page, and often none at all -- as opposed to ABP which injects 20,000 CSS rules into every single web page ([as per ABP developer](https://blog.mozilla.org/nnethercote/2014/05/14/adblock-pluss-effect-on-firefoxs-memory-usage/comment-page-1/#comment-11173)). For example, visiting [www.wired.com](http://www.wired.com/) with matrix filtering turned off, only **one single CSS rule** is injected into the page by HTTPSB.

[**Edit:** after filter coverage has been extended to 99% (from 87%), the number of CSS rules injected into Wired's front page is now eight: `#header + #content > #left > #rlblock_left`, `.displayAd`, `.widget_widget_widgetwiredadtile`, `.WiredWidgetsMarketing`, `#post_nav`, `#magazine_rightRail_A`, `#leaderboard`, `#featured`]

Consider this feature early beta, and as of writing, the support is somewhere around 87% of all cosmetic filters (there is no performance issue or otherwise in supporting the missing filters, it's just a time thing). Note that I didn't spent that much time trying to optimize further than the primary proof-of-concept to show it is possible to improve memory consumption, and improve how fast web pages come to live (not injecting 20,000 CSS rules has a noticeable effect on how fast pages are parsed by the browser).

Here is a first test to compare memory consumption when loading [this page](http://vimcolorschemetest.googlecode.com/svn/html/index-c.html) in the browser:

![Memory: ABP vs HTTPSB](https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/abp-vs-httpsb-mem-test1.png)<br>
<sup>**Important:** If you want to repeat the tests above, be sure that **no other extensions** than the one tested are enabled, as these other extensions may also add their own footprint to the web page. Also, the memory for the web page was forced-garbage-collected before the screenshots (using dev console).</sup>

Note that in the test above, HTTPSB had its default out-of-the-box preset blocked hosts loaded and enabled in the matrix filtering engine, which represents an extra 60,000 filter rules, something not present in ABP. Also, HTTPSB injects two [more](/gorhill/httpswitchboard/blob/master/js/contentscript.js) [scripts](/gorhill/httpswitchboard/blob/master/js/contentscript-uaspoof.js) into every pages and frames as part of its normal operation, these add up too, so the memory footprint could be even (quite I suspect) lower if it wasn't for these two extra content scripts.

Tests for screenshots above was Chromium 34 on Linux 64-bit.

Implementation ([abp-hide-filters.js](/gorhill/httpswitchboard/blob/master/js/abp-hide-filters.js) and [contentscript-elemhide.js](/gorhill/httpswitchboard/blob/master/js/contentscript-elemhide.js)) is rather modular, it doesn't really depend on anything else in HTTPSB except for the utility to extract domain name from a URL, which should be easy enough to replace.