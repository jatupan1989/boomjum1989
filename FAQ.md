Under construction.

#### What does HTTP Switchboard does more than, say, AdBlock+ or AdBlock?
There is [AdBlock](https://chrome.google.com/webstore/detail/adblock/gighmmpiobklfepjocnamgkkbiglidom), and there is [AdBlock Plus](https://chrome.google.com/webstore/detail/adblock-plus/cfhdojbkjhnklbpkdaibdccddilifddb) (which the [EFF advise to install](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)).

If you really care about your privacy, it is good to know what is happening behind a web page, so
I did some tests to compare AdBlock and AdBlock Plus vs HTTP Switchboard. See the differences for yourself when using real web pages, and make an informed choice:

- AdBlock vs HTTP Switchboard:
    * [edition.cnn.com](http://www.diffchecker.com/flic8v70)
    * [nbcpolitics.nbcnews.com](http://www.diffchecker.com/z9byyjng).
- AdBlock Plus (using EFF installation instructions) vs HTTP Switchboard:
    * [edition.cnn.com](http://www.diffchecker.com/jxpdhmit)
    * [nbcpolitics.nbcnews.com](http://www.diffchecker.com/wep03p6r).

Using out of the box settings for *AdBlock* and *HTTP Switchboard*. Using settings suggested by EFF for
*AdBlock Plus*. Note that with *HTTP Switchboard*, the user does not need to explicitly change the cookie settings in chromium/chrome (as required with AdBlock Plus). If cookies are blacklisted for a domain, any outbound cookie will be removed, regardless of chromium/chrome owns settings. 

#### In the top left of the matrix, what is "other"?
So far, here is what I found:
- [favicon.ico](http://en.wikipedia.org/wiki/Favicon)
- [web fonts](http://en.wikipedia.org/wiki/Web_fonts)
- HTML5 [&lt;audio&gt;](http://en.wikipedia.org/wiki/HTML5_Audio) tag
- HTML5 [&lt;video&gt;](http://en.wikipedia.org/wiki/HTML5_video) tag